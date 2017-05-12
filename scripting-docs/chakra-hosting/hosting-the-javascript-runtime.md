---
title: "Hosten der JavaScript-Laufzeit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Hosten der JavaScript-Laufzeit
Die JavaScript Runtime \(JsRT\)\-APIs bieten die Möglichkeit, Desktop\-, Windows Store\- und serverseitigen Anwendungen, die im Windows\-Betriebssystem ausgeführt werden, Skriptfunktionen hinzuzufügen, indem sie die standardbasierte JavaScript\-Engine Chakra verwenden, die auch von Microsoft Edge und Internet Explorer verwendet wird. Diese APIs stehen unter Windows 10 und für jede Version des Windows\-Betriebssystems zur Verfügung, bei der Internet Explorer Version 11.0 installiert ist. Weitere Informationen finden Sie unter [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md). Informationen zum Verwenden von JsRT in Windows Store\-Apps finden Sie unter [JsRT und die universelle Windows-Plattform](#Windows).  
  
> [!NOTE]
>  In dieser Dokumentation wird davon ausgegangen, dass grundlegende Kenntnisse der JavaScript\-Sprache vorhanden sind.  
  
## Konzepte  
 Für das Verständnis des Hostings der JavaScript\-Engine mithilfe der JsRT\-APIs spielen zwei wichtige Konzepte eine Rolle: Laufzeiten und Ausführungskontexte.  
  
 Eine *Laufzeit* stellt eine vollständige JavaScript\-Ausführungsumgebung dar. Jede Laufzeit, die erstellt wird, hat einen eigenen isolierten Heap mit Garbage Collection und standardmäßig ihren eigenen Just\-In\-Time \(JIT\)\-Compilerthread und Garbage Collector \(GC\)\-Thread. Ein *Ausführungskontext* stellt eine JavaScript\-Umgebung mit einem eigenen globalen JavaScript\-Objekt dar, das sich von allen anderen Ausführungskontexten unterscheidet. Eine Laufzeit kann mehrere Ausführungskontexte enthalten, und in solchen Fällen nutzen alle Ausführungskontexte den JIT\-Compiler und den GC\-Thread, die der Laufzeit zugeordnet sind.  
  
 Laufzeiten stellen einen einzigen Ausführungsthread dar. Nur jeweils eine Laufzeit kann auf einem bestimmten Thread aktiv sein, und die Laufzeit kann immer nur auf einem Thread aktiv sein. Für Laufzeiten gelten Threads vom Typ "Rental", sodass eine Laufzeit, die gerade auf keinem Thread aktiv ist \(d. h keinen JavaScript\-Code ausführt oder keine Aufrufe vom Host beantwortet\), auf jedem Thread verwendet werden kann, der nicht bereits eine aktive Laufzeit hat.  
  
 Ausführungskontexte sind an eine bestimmte Laufzeit gebunden und führen Code innerhalb dieser Laufzeit aus. Im Gegensatz zu Laufzeiten können mehrere Ausführungskontexte auf einem Thread gleichzeitig aktiv sein. Somit kann ein Host einen Aufruf an einen Ausführungskontext vornehmen, dieser Ausführungskontext kann einen Rückruf an den Host vornehmen, und der Host kann einen Aufruf an einen anderen Ausführungskontext vornehmen.  
  
 ![Mehrere Ausführungskontexte](../chakra-hosting/media/js-chakra-hosting.png "JS\_Chakra\_Hosting")  
  
 In der Praxis kann ein einzelner Ausführungskontext verwendet werden, es sei denn, ein Host muss Code in separaten Umgebungen ausführen. In ähnlicher Weise ist eine einzelne Laufzeit ausreichend, wenn der Host nicht mehrere Codeabschnitte gleichzeitig ausführen muss.  
  
## Speicherverwaltung  
 JavaScript ist eine Sprache mit Garbage Collection, und somit gelten mehrere Überlegungen, die beim Arbeiten mit den JsRT\-APIs einer anderen Sprache beachtet werden müssen.  
  
 Die Hauptüberlegung ist, dass der JavaScript\-Garbage\-Collector Verweise auf Werte nur an zwei Stellen sehen kann: im Heap der Laufzeit und im Stapel. Daher wird ein Verweis auf einen JavaScript\-Wert, der in einem anderen JavaScript\-Wert oder in einer lokalen Variable im Stapel gespeichert ist, immer vom Garbage Collector gesehen. Verweise, die in anderen Speicherorten gespeichert sind, wie in Heaps, die vom Host oder System verwaltet werden, werden vom Garbage Collector nicht gesehen und führen möglicherweise zur vorzeitigen Auflistung von Werten, die noch vom Host verwendet werden.  
  
> [!IMPORTANT]
>  Einige Sprachcompiler \(wie der C\+\+\-Compiler von Visual Studio\) entfernen lokale Variablen zu Optimierungszwecken wo möglich. Es muss darauf geachtet werden, dass lokale Variablen, die auf JavaScript\-Werte verweisen, sich im Stapel befinden, wenn sie diese Werte aktiv halten sollen.  
  
 Wenn ein Verweis auf einen JavaScript\-Wert an einem Speicherort gespeichert wird, den der Garbage Collector nicht sehen kann, muss der Host mit den JsRT\-APIs Verweise manuell hinzufügen und entfernen.  
  
## Ausnahmebehandlung  
 Wenn eine JavaScript\-Ausnahme während der Skriptausführung auftritt, wird die enthaltene Laufzeit in einen Ausnahmezustand versetzt. Im Ausnahmezustand kann kein Code ausgeführt werden, und alle API\-Aufrufe schlagen mit dem Fehlercode `JsErrorInExceptionState` fehl, bis der Host die Ausnahme mit der `JsGetAndClearException`\-API abruft und löscht. Wenn der Host von einem JavaScript\-Rückruf zurückkehrt, ohne den Ausnahmezustand der Laufzeit gelöscht zu haben, wird die JavaScript\-Ausnahme erneut ausgelöst, sobald die Steuerung wieder an die JavaScript\-Engine übergeben wurde. Dadurch können Hostrückrufe eine JavaScript\-Ausnahme "auslösen", indem die Laufzeit in einen Ausnahmezustand versetzt wird und dann von einem Hostrückruf zurückkehrt.  
  
 Ein Host darf seine eigenen internen Ausnahmen nicht über einen Hostrückruf weitergeben. Alle Rückrufmethoden müssen alle Hostausnahmen abfangen, bevor die Steuerung wieder an die Laufzeit übergeben wird.  
  
## Ressourcenverwendung durch die Laufzeit  
 Die JsRT\-APIs ermöglichen verschiedene Methoden zum Überwachen und Ändern der Ressourcenverwendung durch Laufzeiten. Sie lassen sich grundsätzlich in die folgenden Kategorien einteilen:  
  
-   **Threadverwendung**. Standardmäßig erstellt jede Laufzeit einen dedizierten JIT\-Compiler\-Thread und einen dedizierten GC\-Thread, die die Laufzeit verarbeiten. Wenn eine Laufzeit mit dem Flag `JsRuntimeAttributeDisableBackgroundWork` erstellt wird, werden die JIT\- und GC\-Aufgaben auf dem Laufzeitthread selbst und nicht auf separaten Hintergrundthreads ausgeführt. Ein Host kann auch einen Threaddienstrückruf für den `JsCreateRuntime`\-Aufruf bereitstellen, was es dem Host ermöglicht, JIT\- und GC\-Aufgaben optimal zu planen.  
  
-   **Speichernutzung**. Es gibt mehrere Methoden, die Speichernutzung einer Laufzeit zu überwachen und zu ändern. Wenn die Laufzeit über einen längeren Zeitraum ausgeführt wird, kann der Host beim Erstellen der Laufzeit das Flag `JsRuntimeAttributeEnableIdleProcessing` angeben und anschließend `JsIdle` aufrufen, wenn sich der Host im Leerlauf befindet. Hierdurch kann die Engine einige Arbeitsspeicherbereinigungs\- und Verwaltungsaufgaben auf eine Leerlaufzeit verschieben.  
  
     Der Host kann Garbage Collections durch den Aufruf von `JsSetRuntimeBeforeCollectCallback` überwachen. Er kann auch vom Heap vorgenommene Speicherbelegungen überwachen, indem er `JsSetRuntimeMemoryAllocationCallback` aufruft. Beachten Sie, dass diese API nicht bei jeder JavaScript\-Speicherbelegung einen Rückruf vornimmt, sondern nur, wenn der Heap der Laufzeit mehr Platz für die Speicherbelegung beansprucht. Der Speicherbelegungsrückruf kann die Anforderung verweigern, was eine Garbage Collection und, wenn kein Arbeitsspeicher verfügbar ist, einen Fehler aufgrund von ungenügendem Arbeitsspeicher in der Laufzeit auslöst.  
  
     Der Host kann außerdem `JsSetRuntimeMemoryLimit` aufrufen, um eine Begrenzung für die Arbeitsspeicherbelegung durch die Laufzeit festzulegen. Wenn eine Laufzeit die Grenze erreicht, löst sie eine Garbage Collection aus, und wenn kein Arbeitsspeicher verfügbar ist, wird ein Fehler aufgrund von ungenügendem Arbeitsspeicher von der Laufzeit ausgelöst.  
  
-   **Skriptunterbrechung und \-auswertung**. Der Host kann `JsDisableRuntimeExecution` aufrufen, um die Ausführung in einer Laufzeit zu beenden. Dieser Aufruf kann jederzeit und von jedem Thread gemacht werden. Da die Skriptbeendigung vom Erreichen von Wächterpunkten im Code abhängt, wird ein Skript möglicherweise nicht genau zum gewünschten Zeitpunkt, sondern unmittelbar danach beendet. Standardmäßig werden Wächterpunkte für die Beendigung konservativ in den generierten Code eingefügt und decken möglicherweise nicht jede Situation ab, wie z. B. Endlosschleifen. Das Erstellen der Laufzeit mit dem Flag `JsRuntimeAttributeAllowScriptInterrupt` bewirkt, dass die Laufzeit zusätzliche Überprüfungen für Endlosschleifen einfügt, wodurch allerdings häufig ein kleiner Leistungsoverhead entsteht.  
  
     Wenn ein Host die Generierung von systemeigenem Code durch den JIT\-Compiler verhindern möchte, kann er das `JsRuntimeAttributeDisableNativeCodeGeneration`\-Flag angeben. Ein Host kann außerdem verhindern, dass Skripts selbst dynamisch Skripts ausführen, indem er das `JsRuntimeAttributeDisableEval` angibt.  
  
## Debuggen und Profilerstellung  
 JsRT\-APIs unterstützen Debugging und Profilerstellung über die Active Scripting\-Technologie.  
  
 Ab Windows 10 unterstützt die JavaScript\-Engine Chakra ein Legacy\-Modul und ein Edge\-Modul. Weiterhin können Sie JsRT als Ausrichtung verwenden \(siehe [Ansteuern des Edgemodus im Vergleich zu Legacy\-Modulen](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) für ausführliche Informationen\). Das Debuggen eines Skripts in Visual Studio funktioniert beim Legacy\-Modul und Edge\-Modul unterschiedlich. Beim Legacy\-Modul muss der Host einen [IDebugApplication\-Schnittstelle](../winscript/reference/idebugapplication-interface.md)\-Zeiger bereitstellen, der von einer [IProcessDebugManager\-Schnittstelle](../winscript/reference/iprocessdebugmanager-interface.md)\-Instanz abgerufen werden kann. Beim Edge\-Modul ist `IDebugApplication` veraltet, und die Chakra\-Engine ermöglicht systemeigene und Skriptdebuggingfunktionen mithilfe des Visual Studio\-Debuggers, ohne dass eine Implementierung von `IDebugApplication` vom Benutzer erforderlich ist.  
  
 Um Skripts in einem Ausführungskontext debugfähig zu machen, muss die Chakra\-Engine weniger effiziente Codeausführungsmethoden verwenden. Daher dauert die Ausführung von debugfähigem Code in der Regel länger als die von nicht debugfähigem Code. Folglich kann mithilfe des Legacy\-Moduls ein Host entweder das Debuggen in einem Ausführungskontext am Anfang starten, indem er gleich den `IDebugApplication`\-Zeiger über `JsCreateContext` bereitstellt, oder er kann warten, bis der Debugvorgang erforderlich wird, und dann `JsStartDebugging` aufrufen. Beim Edge\-Modul verwendet `JsCreateContext` keinen `IDebugApplication`\-Parameter mehr, und daher ist das Skript nur debugfähig, wenn `JsStartDebugging` aufgerufen wird. Beim Debuggen mit Visual Studio muss die "Skript"\-Debuggeroption aktiviert werden.  
  
 Die Profilerstellung für JavaScript\-Code in einem Ausführungskontext kann auf zwei Arten erfolgen. Der Visual Studio\-Profiler der Befehlszeile \(vsperf.exe\) kann in Windows 8.1 und höheren Versionen mit dem \/js\-Schalter verwendet werden, um einen Bericht zur JavaScript\-Codeausführung in der Anwendung zu erzeugen. Oder der Host kann `JsStartProfiling` und `JsStopProfiling` direkt aufrufen und einen Rückruf bereitstellen, um die Profilerstellung selbst auszuführen. Der Host kann auch den Zustand des Heaps mit Garbage Collection untersuchen, indem er `JsEnumerateHeap` aufruft. Die Profilerstellung in JsRT funktioniert auf die gleiche Weise beim Legacy\-Modul und Edge\-Modul. Allerdings sind die JsRT\-Profilerstellungs\-APIs \(`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap` und `JsIsEnumeratingHeap`\) nicht für universelle Windows\-Apps verfügbar.  
  
<a name="Windows"></a>   
## JsRT und die universelle Windows\-Plattform  
 Mit JsRT\-APIs können Sie einer universellen Windows\-App Skriptfunktionen hinzufügen. Eine universelle Windows\-App, die die JsRT\-APIs verwendet, muss auf die Edge\-JSRT\-APIs ausgerichtet sein, die wiederum auf die Edge\-Chakra\-Engine ausgerichtet sind. Weitere Informationen finden Sie unter [Ansteuern des Edgemodus im Vergleich zu Legacy\-Modulen](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md). Die gesamte JsRT\-API ist für universelle Windows\-Apps verfügbar, mit Ausnahme der Profilerstellung und Unterstützung der Heapenumeration \(`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap` und `JsIsEnumeratingHeap` werden nicht unterstützt\).  
  
 Mithilfe von JsRT können Skripts auch alle [universellen Windows\-Plattform\-APIs \(UWP\)](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) direkt aufrufen, nachdem der API\-Namespace über die Edge\-JsRT\-API `JsProjectWinRTNamespace` verfügbar gemacht wurde. Während für universelle Windows\-Anwendungen kein Setup zusätzlich zum Projizieren von erforderlichen Namespaces erforderlich ist, muss in einer klassischen Windows\-Anwendung \(Win32\) ein COM\-initialisierter delegierter Verteilungsmechanismus über `JsSetProjectionEnqueueCallback` aktiviert werden, um Ereignisse und asynchrone APIs zu aktivieren. Im folgenden Win32\-Beispiel werden asynchrone UWP\-APIs verwendet, um einen HTTP\-Client zum Abrufen von Inhalten aus einem URI zu erstellen:  
  
```cpp  
typedef struct _jsCall { JsProjectionCallback jsCallback; JsProjectionCallbackContext jsContext; HANDLE event; } jsCall; // Set up delegated pumping mechanism; not necessary in UWP applications. jsCall outstandingCall = {}; CoInitializeEx(nullptr, COINIT_MULTITHREADED); JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback, JsProjectionCallbackContext jsContext, void *callbackState) { jsCall* call = (jsCall*)callbackState; call->jsCallback = jsCallback; call->jsContext = jsContext; SetEvent(call->event); }, &outstandingCall); HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS); outstandingCall.event = event; // Project necessary namespaces. JsProjectWinRTNamespace(L"Windows.Foundation"); JsProjectWinRTNamespace(L"Windows.Web"); // Get content from an Uri. JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \ L"var httpClient = new Windows.Web.Http.HttpClient();" \ L"httpClient.getStringAsync(uri).done(function (content) { " \ L"    // do something with the string content " \ L"}, onError); " \ L"function onError(reason) { " \ L"    // error handling " \ L"}", currentSourceContext, L"", &result); // Wait for async call to come in and then execute; not necessary in UWP applications. WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0; outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## Siehe auch  
 [JavaScript\-Laufzeit – Beispiel\-App](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)   
 [JavaScript\-Laufzeithosting](../chakra-hosting/javascript-runtime-hosting.md)