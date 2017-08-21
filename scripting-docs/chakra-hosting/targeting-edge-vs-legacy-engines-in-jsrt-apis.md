---
title: Ansteuern des Edgemodus im Vergleich zu Legacy-Modulen in JsRT-APIs | Microsoft-Dokumentationen
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 50947cbd619f086daecc1e09f88a4b238a36ee41
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="targeting-edge-vs-legacy-engines-in-jsrt-apis"></a>Ansteuern des Edgemodus im Vergleich zu Legacy-Modulen in JsRT-APIs
Ab Windows 10 besteht eine der Änderungen, die wir an dem JavaScript-Modul Chakra, das auf die Windows 10-Browserstrategie zur Unterstützung eines neuen Edge-Renderingmoduls ausgerichtet ist, darin, zwei unterschiedliche Chakra-Module zu unterstützen:  
  
-   Das alte Chakra-Modul (auch als *Legacymodul* oder „jscript9.dll“ bezeichnet), das mit Internet Explorer 11 ausgeliefert wird und diesen Browser unterstützt. Dieses Modul ist zeitlich fixiert und wird in Win8.1/IE11 im Prinzip unverändert bleiben.  
  
-   Das neue Chakra-Modul (auch als *Edge-Modul* oder „chakra.dll“ bezeichnet), das mit dem neuen Browser in Windows 10, Microsoft Edge, ausgeliefert wird und diesen unterstützt. Dieses Modul wird laufend aktualisiert und unterstützt ein „lebendes“ [Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx)-Modul. Ein „lebendes“ Edge-Modul impliziert, dass das Edge-Modul im Gegensatz zum Legacymodul keine Form von Versionsverwaltung für optionale Skriptfunktionalität bietet.  
  
 Beim Erstellen einer App mit der JavaScript Runtime Hosting (JsRT)-API können Sie sich entweder auf das Legacy- oder auf das Edge-Modul konzentrieren.  
  
-   Wenn Sie Abwärtskompatibilität mit Ihren vorhandenen Anwendungen benötigen, verwenden Sie das Legacymodul.  
  
-   Wenn Ihre App vorwärts gerichtet sein und neue JavaScript-Funktionen bei der Veröffentlichung unterstützen soll (z. B. ECMAScript 6), verwenden Sie das Edge-Modul.  
  
 Dieses Thema enthält Informationen, die beschreiben, wie Sie die verschiedenen Module verwenden.  
  
## <a name="target-your-preferred-version"></a>Verwenden der bevorzugten Version  
 Wenn Sie eine App erstellen, können Sie die Version der JsRT auswählen, die das Edge-Modul oder das Legacymodul unterstützt. Sie können die JsRT-Version basierend auf den oben aufgeführten Richtlinien auswählen. Um diese Unterschiede zu berücksichtigen, wurden die folgenden Änderungen an `JsCreateRuntime`, `JsCreateContext`und `JsStartDebugging`vorgenommen.  
  
 Für `JsCreateRuntime`:  
  
-   Wenn Sie das Legacymodul verwenden möchten, ist der `JsRuntimeVersionEdge` -Enumerationswert veraltet, und eine Nachricht empfiehlt, stattdessen den `JsRuntimeVersionInternetExplorer11` -Wert zu verwenden.  
  
-   Wenn Sie das Edge-Modul verwenden möchten, wird der Versionsparameter in der `JsCreateRuntime` -Funktion ausgelassen.  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 Für `JsCreateContext` und `JsStartDebugging`:  
  
-   Wenn Sie das Legacymodul verwenden, wird die `IDebugApplication` -Schnittstelle verwendet, um Ihre eigenen Nicht-remote-Debuggingmethoden anzugeben. Für das Debuggen verwenden die `JsCreateContext` - und `JsStartDebugging` -Funktionen `IDebugApplication` als Parameter.  
  
-   Wenn Sie das Edge-Modul verwenden, ist die `IDebugApplication` -Schnittstelle veraltet. Die Chakra-Engine ermöglicht systemeigene und Skriptdebuggingfunktionen mithilfe des Visual Studio-Debuggers, ohne dass eine Implementierung von `IDebugApplication` vom Benutzer erforderlich ist. Die Schnittstelle ist als Ergebnis kein Parameter für `JsCreateContext` und `JsStartDebugging` mehr.  
  
 Die Signaturen für die obigen APIs im Legacymodul lauten wie folgt:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 Die Signaturen für die obigen APIs im Edge-Modul lauten wie folgt:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## <a name="compile-for-your-preferred-version-using-visual-c"></a>Kompilieren für die bevorzugte Version mit Visual C++  
 Importieren Sie bei Verwendung von Visual C++ die JsRT-API, indem Sie den „jsrt.h“-Header einschließen, und stellen Sie sicher, dass „jsrt.lib“ in der Dateiliste der Linker enthalten ist:  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![Hinzufügen von „jsrt.lib“ als Linkereingabedatei](../chakra-hosting/media/js-chakra.png "JS_Chakra_")  
  
 Wenn Sie die Binärdateien des Edge-Moduls verwenden möchten, müssen Sie das Makro `USE_EDGEMODE_JSRT` definieren, bevor Sie „jsrt.h“ einschließen, und statt mit „jsrt.lib“ sollten Sie mit „chakrart.lib“ verknüpfen:  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![Hinzufügen von „chakrart.lib“ als Linkereingabedatei](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting_")  
  
 Wenn Sie eine neue Anwendung starten, können Sie jetzt Code für die JsRT-API schreiben.  
  
## <a name="compile-for-your-preferred-version-using-net"></a>Kompilieren für die bevorzugte Version mit .NET  
 Wenn Sie .NET und P/Invoke verwenden, müssen Sie zum Importieren von „chakra.dll“ anstelle von „jscript9.dll“ die JsRT-API-Deklarationen [DllImport] ändern. Ändern Sie außerdem die Definition von `JsCreateRuntime` zum Entfernen des `JsRuntimeVersion` -Parameters und die Definition von `JsCreateContext` und `JsStartDebugging` zum Entfernen des `IDebugApplication` -Parameters.  
  
 Verwenden Sie den folgenden Code für das Legacymodul.  
  
```c#  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 Verwenden Sie den folgenden Code für das Edge-Modul.  
  
```c#  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  Wenn Sie ein manuelles Marschalling für den Funktionszeiger ausführen (z. B. über LoadLibrary/GetProcAddress), ist es wichtig, dass Sie die Deklarationen der Methode nicht mischen, andernfalls verliert der Stapel das Gleichgewicht, was zu unvorhersehbarem Verhalten führt, z. B. wenn der Absturz Ihrer App verursacht wird. Das gleiche Problem tritt auf, wenn Sie in Ihrem Importcode ein globales Suchen und Ersetzen von Instanzen von „jscript9.dll“ durchführen, da der `version`-Parameter nicht gelöscht wird.  
  
## <a name="summary"></a>Zusammenfassung  
 In Windows 10 werden die JavaScript-Laufzeithosting-APIs in zwei Teile geteilt. Diese APIs unterstützen jetzt ein „lebendes“ Edge-Modul, dessen Sprachfunktionen an das „lebende“ Edge-Modul in Microsoft Edge ausgerichtet sind. Sie können diese Funktionen von Ihren Desktop- oder Store-Apps aus nutzen, um neue und interessante Möglichkeiten zu schaffen, Ihre Anwendung zu erweitern und in Ihrer vorhandenen Codebasis moderne Webfähigkeiten zu nutzen. Da es allerdings feine Unterschiede zwischen früheren Versionen gibt, müssen Sie die folgenden Punkte beachten, wenn Sie sich für das Edge-Modul oder das Legacymodul entscheiden.  
  
-   Ihre App kann nur eine Version von JsRT pro Prozess unterstützen.  
  
     Sie können beispielsweise keine Edge-Modullaufzeit und anschließend eine Legacy-Modullaufzeit erstellen und davon ausgehen, dass sie ordnungsgemäß in demselben Prozess ausgeführt werden. Dies wird nicht unterstützt und kann zu nicht dokumentiertem Verhalten führen, z. B. zu einem Fehler beim Laden der zweiten DLL.  
  
-   Wenn Sie das Edge-Modul verwenden, kann Ihre App unerwartet neue Features abrufen, wenn die zugrunde liegende Plattform automatisch aktualisiert wird.  
  
     Beispielsweise unterstützt der Internet Explorer 11-Modus der Legacylaufzeit Blockbereichs-Variablendeklarationen wie `let` und `const`. Wenn das automatische Versionsverwaltungsverhalten des Edge-Moduls zuvor der Standard gewesen wäre, wäre Code, der im Internet Explorer 10-Modus funktioniert hätte, der keine Blockbereichsdefinitionsregeln besaß, möglicherweise fehlgeschlagen, wenn die Plattform automatisch aktualisiert worden wäre. Dies muss berücksichtigt werden, wenn Sie sich für ein Laufzeitmodell entscheiden. Obwohl wir der Meinung sind, dass Sie möglichst das Edge-Modul verwenden sollten, müssen Sie beim Verwenden der JavaScript-Codestrukturen, die in der Zukunft ungültig werden können, mit Bedacht vorgehen.  
  
-   JsRT für den Windows Store unterstützt nur das Edge-Modul (chakra.dll). Die Zertifizierung von Apps, die versuchen, eine JsRT-API in „jscript9.dll“ zu verknüpfen, schlägt fehl.  
  
-   Es ist wichtig, dass Sie die Deklaration von `JsCreateRuntime`, `JsCreateContext`und `JsStartDebugging` zwischen „jscript9.dll“ und „chakra.dll“ nicht verwechseln, da der Stapel auf diese Weise das Gleichgewicht verliert.  
  
     Bei Verwendung von C und C++ erhalten Sie einen Linkerfehler, wenn Sie versuchen, die falsche Deklaration zu verwenden, solange Sie nicht etwa `LoadLibrary` und dann `GetProcAddress` aufrufen. .NET-Entwickler finden dieses Problem möglicherweise nicht so leicht. Überprüfen Sie daher Ihren Code, wenn Sie diese Funktion verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Laufzeithosting](../chakra-hosting/javascript-runtime-hosting.md)
