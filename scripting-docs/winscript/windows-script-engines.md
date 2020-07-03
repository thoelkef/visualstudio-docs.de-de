---
title: Windows Script-Engines | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27a500f9df91738e2db563f7e37ee646925b674e
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835692"
---
# <a name="windows-script-engines"></a>Windows Script-Engines
Um eine Windows Script-Engine zu implementieren, erstellen Sie ein OLE COM-Objekt, das die folgenden Schnittstellen unterstützt.  
  
|||  
|-|-|  
|Schnittstelle|BESCHREIBUNG|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Bietet grundlegende Skriptmöglichkeiten. Die Implementierung dieser Schnittstelle ist erforderlich.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Bietet die Möglichkeit, Skripttext hinzuzufügen, Ausdrücke auszuwerten usw. Die Implementierung dieser Schnittstelle ist optional. Wenn sie allerdings nicht implementiert ist, muss die Skript-Engine eine der IPersist*-Schnittstellen implementieren, um ein Skript zu laden.|  
|IPersist*|Bietet Persistenzunterstützung. Die Implementierung mindestens einer der folgenden Schnittstellen ist erforderlich, wenn [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nicht implementiert ist.<br /><br /> IPersistStorage: bietet Unterstützung für das Attribut DATA={url} im OBJECT-Tag.<br /><br /> IPersistStreamInit: bietet Unterstützung für das gleiche wie `IPersistStorage` sowie für das Attribut DATA="string-encoded byte stream" im OBJECT-Tag.<br /><br /> IPersistPropertyBag: bietet Unterstützung für das Attribut PARAM= im OBJECT-Tag.|  
  
> [!NOTE]
> Es ist möglich, dass die Skript-Engine nie aufgerufen wird, um einen Skriptzustand mit `IPersist*` zu speichern oder wiederherzustellen. Stattdessen wird [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) verwendet, indem [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) aufgerufen wird, um ein leeres Skript zu erstellen. Anschließend werden Scriptlets hinzugefügt und mit [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) mit Ereignissen verbunden, und allgemeiner Code wird mit [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) hinzugefügt. Nichtsdestoweniger sollte eine Skript-Engine mindestens eine `IPersist*`-Schnittstelle (bevorzugt `IPersistStreamInit`) vollständig implementieren, da andere Hostanwendungen diese möglicherweise verwenden möchten.  
  
 In den folgenden Abschnitten wird die Implementierung einer Windows-Skript-Engine ausführlicher beschrieben.  
  
 Weitere Informationen finden Sie in der [Referenz zu Windows-Skriptschnittstellen](../winscript/reference/windows-script-interfaces-reference.md).  
  
## <a name="registry-standard"></a>Registrierungsstandard  
 Eine Windows-Skript-Engine kann durch Kategoriebezeichner identifiziert werden. Windows-Skript definiert aktuell zwei Kategoriebezeichner.  
  
|||  
|-|-|  
|Kategorie|Beschreibung|  
|CATID_ActiveScript|Gibt an, dass die Klassen Bezeichner (CLSIDs) Windows-Skript-Engines sind, die mindestens die [IActiveScript](../winscript/reference/iactivescript.md) -Schnittstelle und einen Persistenzmechanismus (die- `IPersistStorage` ,- `IPersistStreamInit` oder IPersistPropertyBag-Schnittstelle) unterstützen.|  
|CATID_ActiveScriptParse|Gibt an, dass die CLIDs Windows-Skript-Engines sind, die mindestens die Schnittstellen [IActiveScript](../winscript/reference/iactivescript.md) und [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) unterstützen|  
  
 Obwohl [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) kein echter Persistenzmechanismus ist, unterstützt er die [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md)-Methode, deren Funktion der von `IPersist*::InitNew` entspricht.  
  
## <a name="script-engine-states"></a>Skript-Engine-Zustände  
 Eine Windows-Skript-Engine kann sich immer in mehreren Zuständen befinden.  
  
|||  
|-|-|  
|State|Beschreibung|  
|nicht initialisierte|Das Skript wurde nicht mit der Schnittstelle IPersist* initialisiert oder geladen, oder es wurde keine [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)-Schnittstelle festgelegt. Die Skript-Engine kann in diesem Zustand prinzipiell nicht verwendet werden, bis das Skript geladen wird.|  
|initialisiert|Das Skript wurde mit der `IPersist*`-Schnittstelle initialisiert und die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)-Schnittstelle ist festgelegt, aber nicht mit Hostobjekten und Senkereignissen verbunden. Beachten Sie, dass dieser Zustand einfach bedeutet, dass die Methoden `IPersist*::Load`, `IPersist*::InitNew` oder [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) abgeschlossen wurden, und dass die [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md)-Methode aufgerufen wurde. Die Engine kann in diesem Modus keinen Code ausführen. Die Engine fügt Code einer Warteschlange hinzu, den der Host mit der [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)-Methode übergibt, und führt den Code aus, nachdem es zum Anfangszustand übergegangen ist.<br /><br /> Weil Sprachen bei der Semantik stark variieren können, ist es nicht erforderlich, dass Skript-Engines diesen Statusübergang unterstützen. Engines, die die [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)-Methode unterstützen müssen diesen Statusübergang allerdings unterstützen. Hosts müssen sich auf diesen Übergang vorbereiten und entsprechende Maßnahmen ergreifen: die aktuelle Skript-Engine veröffentlichen, neue Skript-Engines erstellen und `IPersist*::Load`, `IPersist*::InitNew` oder [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) aufrufen (und möglicherweise auch noch [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). Das Verwenden des Übergangs kann als Optimierung der oben stehenden Schritte angesehen werden. Beachten Sie, dass alle Informationen, die die Skript-Engine zu den Namen der benannten Elemente abgerufen hat, und die Typinformationen, die die benannten Elemente beschreiben, ihre Gültigkeit nicht verlieren.<br /><br /> Da Sprachen deutlich variieren, ist die Definition der Semantik dieses Übergangs schwierig. Es muss mindestens die Verbindung der Skript-Engine mit allen Ereignissen getrennt werden. Zudem muss die Engine alle SCRIPTINFO_IUNKNOWN-Zeiger freigeben, die durch den Aufruf der [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md)-Methode erhalten wurden. Die Engine muss die Zeiger erneut abrufen, nachdem das Skript ausgeführt wurde. Die Skript-Engine sollte darüber hinaus das Skript in den ursprünglichen Zustand zurückversetzen, der der Sprache angemessen ist. VBScript setzt z.B. alle Variablen zurück und behält jeden Code bei, der dynamisch durch den Aufruf von [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) mit festgelegtem SCRIPTTEXT_ISPERSISTENT-Flag hinzugefügt wurde. Andere Sprachen müssen möglicherweise aktuelle Werte beibehalten (wie z.B. Lisp, da es keine Trennung von Code und Daten gibt) oder in einen bekannten Zustand zurückversetzt werden (dies gilt auch für Sprachen mit statisch initialisierten Variablen).<br /><br /> Beachten Sie, dass der Übergang zum Zustand „Gestartet“ die gleiche Semantik (d.h. die Skript-Engine sollte im gleichen Zustand bleiben) wie ein Aufruf von `IPersist*::Save` haben sollte, um die Skript-Engine zu speichern. Anschließend sollte `IPersist*::Load` aufgerufen werden, um eine neue Skript-Engine zu laden. Diese Aktionen sollten die gleiche Semantik wie [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) aufweisen. Skript-Engines, die `IActiveScript::Clone` oder `IPersist*` noch nicht unterstützen, sollten genau abwägen, wie sich der Übergang zum Zustand „Gestartet“ verhalten sollte, sodass ein derartiger Übergang nicht gegen die oben stehenden Bedingungen verstößt, wenn die Unterstützung für `IActiveScript::Clone` oder `IPersist*` später hinzugefügt wurde.<br /><br /> Während dieses Übergangs zum Zustand „Gestartet“ unterbricht die Skript-Engine die Verbindung zu Ereignissenken, nachdem die entsprechenden Destruktoren usw. im Skript ausgeführt wurden. Um die Ausführung dieser Destruktoren zu verhindern, kann der Host das Skript zunächst in den Zustand „Getrennt“ versetzen, bevor es zum Zustand „Gestartet“ übergeht.<br /><br /> Verwenden Sie [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), um einen ausgeführten Skriptthread abzubrechen, ohne darauf zu warten, dass aktuelle Ereignisse usw. fertig ausgeführt werden.|  
|gestartet|Der Übergang vom Zustand „Initialisiert“ zum Zustand „Gestartet“ führt dazu, dass die Engine jeden Code ausführt, der im Zustand „Initialisiert“ der Warteschlange hinzugefügt wurde. Die Engine kann Code im Zustand „Gestartet“ ausführen, aber es besteht keine Verbindung zu Ereignissen, die mit der [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md)-Methode hinzugefügt wurden. Die Engine kann Code ausführen, indem sie die IDispatch-Schnittstelle aufruft, die von der [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md)-Methode erhalten wurde, oder durch einen Aufruf von [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Es ist möglich, dass weitere Initialisierungen im Hintergrund fortlaufen (progressives Laden), und dass ein Aufruf der [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md)-Methode mit festgelegtem SCRIPTSTATE_CONNECTED-Flag dazu führt, dass das Skript blockiert ist, bis die Initialisierung abgeschlossen ist.|  
|connected|Das Skript wird geladen und für Senkereignisse von Hostobjekten verbunden. Wenn es sich dabei um einen Übergang vom Zustand „Initialisiert“ handelt, sollte die Skript-Engine über den Zustand „Gestartet“ übergehen und die nötigen Aktionen ausführen, bevor sie in den Zustand „Verbunden“ übergeht und eine Verbindung mit Ereignissen herstellt.|  
|getrennt|Das Skript wird geladen und befindet sich in einem Laufzeitzustand, wird aber vorübergehend von Senkereignissen von Hostobjekten getrennt. Dies erfolgt entweder logisch (erhaltene Ereignisse werden ignoriert) oder physisch (IConnectionPoint::Unadvise wird auf den entsprechenden Verbindungspunkten aufgerufen). Wenn es sich dabei um einen Übergang vom Zustand „Initialisiert“ handelt, sollte die Skript-Engine über den Zustand „Gestartet“ übergehen und die nötigen Aktionen ausführen, bevor sie in den Zustand „Getrennt“ übergeht. Ereignissenken, die sich in Bearbeitung befinden, werden abgeschlossen, bevor der Zustand sich ändert. Verwenden Sie [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), um einen ausgeführten Skriptthread abzubrechen. Dieser Zustand unterscheidet sich dahingehend vom Zustand „Initialisiert“, als dass der Übergang zu diesem Zustand nicht zum Zurücksetzen des Skripts führt. Darüber hinaus wird auch nicht der Laufzeitzustand des Skript zurückgesetzt, und die Prozedur der Skriptinitialisierung wird nicht ausgeführt.|  
|closed|Das Skript wurde geschlossen. Die Skript-Engine funktioniert nicht mehr und gibt für die meisten Methoden Fehler zurück.|  
  
 In der folgenden Abbildung werden die Beziehungen zwischen den verschiedenen Skript-Engine-Zuständen sowie die Methoden, die die Übergange vom einen in den anderen Zustand auslösen, veranschaulicht.  
  
 In der folgenden Abbildung werden die Aktionen veranschaulicht, die die Skript-Engine während der verschiedenen Statusübergänge durchführt.  
  
## <a name="scripting-engine-threading"></a>Skript-Engine-Threading  
 Da die Windows-Skript-Engine in vielen Umgebungen eingesetzt werden kann, ist es wichtig, dass Sie sein Ausführungsmodel so flexibel wie möglich gestalten. Ein serverbasierter Host muss möglicherweise einen Multithreadentwurf aufrechterhalten, während Windows-Skript effizient verwendet wird. Gleichzeitig sollte ein Host, der kein Threading verwendet, wie z.B. eine typische Anwendung, nicht durch die Threadingverwaltung belastet werden. Windows-Skript erreicht dieses Gleichgewicht, indem es die Möglichkeiten einschränkt, mit denen eine Freethread-Skript-Engine einen Rückruf des Hosts durchführen kann, sodass diesem diese Last genommen wird.  
  
 Skript-Engines, die auf Servern verwendet werden, werden üblicherweise als Freethread-COM-Objekte implementiert. Dies bedeutet, dass Methoden auf der [IActiveScript](../winscript/reference/iactivescript.md)-Schnittstelle und deren verknüpften Schnittstellen von einem Thread während des Prozesses aufgerufen werden können, ohne das Marshalling nötig ist. (Leider bedeutet dies auch, dass die Skript-Engine als Prozess interner Server implementiert werden muss, da OLE das prozessübergreifende Marshalling von frei Thread Objekten derzeit nicht unterstützt.) Die Synchronisierung ist die Verantwortung der Skript-Engine. Für Skript-Engines, die nicht intern eintrittsvariant sind, oder Sprachmodelle, die keine Multithreadmodelle sind, kann die Synchronisierung z.B aus einer einfachen Serialisierung des Zugriffs auf die Skript-Engine mit einem Mutex bestehen. Selbstverständlich sollten bestimmte Methoden, wie z.B. [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), nicht so serialisiert werden, damit ein hängendes Skript von einem anderen Thread beendet werden kann.  
  
 Die Tatsache, dass [IActiveScript](../winscript/reference/iactivescript.md) normalerweise ein Freethreadskript ist, impliziert für gewöhnlich, dass die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)-Schnittstelle und das Objektmodell des Hosts auch Freethread sein sollten. Dies würde die Implementierung eines Host erschweren, besonders im häufigen Fall, wenn der Host eine Windows-basierte Anwendung mit einem Thread ist, die ActiveX-Apartmentmodell-Steuerelemente oder Steuerelemente mit einem Thread in ihrem Objektmodell enthält. Aus diesem Grund wird das Verwenden von [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) durch die Skript-Engine folgendermaßen eingeschränkt:  
  
 Die Skriptwebsite wird immer im Kontext des Hostthreads aufgerufen. Das bedeutet, dass die Skript-Engine nie die Skriptwebsite im Kontext eines Threads aufruft, der von der Skript-Engine erstellt wurde, sondern nur innerhalb einer Skript-Engine-Methode, die vom Host über [IActiveScript](../winscript/reference/iactivescript.md) und dessen Derivate, über das offengelegte Verteilungsobjekt der Skript-Engine, über eine Windows-Meldung oder von einer Ereignisquelle im Objektmodell des Hosts aufgerufen wurde.  
  
 Die Skriptwebsite wird die aus dem Kontext einer einfachen Methode zur Steuerung des Threadzustands aufgerufen ([IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)-Methode) oder der [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows-Skriptschnittstellen](../winscript/windows-script-interfaces.md)
