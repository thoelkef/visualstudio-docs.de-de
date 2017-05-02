---
title: "Windows-Skriptschnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows-Skriptschnittstellen
Microsoft Windows\-Skript\-Schnittstellen bieten eine Möglichkeit, sodass eine Anwendung Skripterstellung und OLE\-Automatisierung hinzugefügt wird.  Skipthosts, die auf Windows Script basieren, können Skriptmodule aus mehreren Quellen und Anbietern verwenden, um Skripterstellung zwischen Komponenten zu verwalten.  Das Skriptanbieter die Implementierung der Skriptselbstsprache, Syntax, persistentes Format, Ausführungsmodell und so auf\-wird überlassen.  
  
 Windows Script\-Dokumentation ist in folgende Abschnitte unterteilt:  
  
 [Windows Script Hosts](../winscript/windows-script-hosts.md)  
  
 [Windows Script\-Module](../winscript/windows-script-engines.md)  
  
 [Debuggen mit Active Script \- Übersicht](../winscript/active-script-debugging-overview.md)  
  
 [Active Script\-Profilerstellung \- Übersicht](../winscript/active-script-profiling-overview.md)  
  
 [Windows Script\-Schnittstellenverweis](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Windows Script\-Hintergrund  
 Windows Script\-Schnittstellen lassen sich in zwei Kategorien: Windows Script Host und Windows Script\-Module.  Ein Host erstellt ein Skriptmodul und Aufrufe auf Modul\-, um die Skripts auszuführen.  Beispiele für Windows Script Host\-Einschließung:  
  
-   Microsoft Internet Explorer  
  
-   Internet\-Entwicklungstoole  
  
-   Shell  
  
 Windows Script\-Module können für jede Sprache oder Laufzeitumgebung entwickelt wurden und einschließen:  
  
-   Microsoft Visual Basic Scripting Edition \(VBScript\)  
  
-   Perl  
  
-   Lisp  
  
 Um Implementierung vom Host so flexibel auszuführen bereitgestellt wie möglich, wird ein OLE\-Automatisierungs\-Wrapper für Windows Script.  hat jedoch ein Host, der dieses Wrapperobjekt verwendet, um das Skriptmodul zu instanziieren, nicht den Grad des Steuerelements über dem Ablaufnamespace, das Persistenzmodell usw. dass er wurde, wenn er Windows Script direkt verwendet.  
  
 Der Windows Script\-Entwurf sucht die Schnittstellenelemente, die nur einer Erstellungsumgebung, benötigt werden nonauthoring Hosts \(wie Browser und Viewer\) und Skriptmodule \(beispielsweise, VBScript\) können einfach gehalten werden.  
  
## Windows Script\-grundlegende Architektur  
 Die folgende Abbildung zeigt die Interaktion zwischen einem Windows Script Host und einem Windows Script\-Modul an.  
  
 Die Schritte, die in die Interaktion zwischen dem Host und dem Modul gehören, werden in der folgenden Liste an.  
  
1.  Erstellen Sie ein Projekt.  Der Host lädt ein Projekt oder ein Dokument.  \(Dieser Schritt ist nicht zum Windows Script bestimmt, jedoch wird der Vollständigkeit halber hier enthalten\).  
  
2.  Stellen Sie das Windows Script\-Modul erstellt.  Der Host ruft `CoCreateInstance` auf, um ein neues Windows Script\-Modul erstellen und gibt die Klassenbezeichner \(CLSID\) des bestimmten Skriptmoduls an, um zu verwenden.  Beispielsweise empfängt der HTML\-Browser von Internet Explorer die Klassen\-ID des Skriptmoduls durch das CLSID\=\-Attribut des Tags HTML \<OBJECT\>.  
  
3.  Laden Sie das Skript.  Wenn der Skriptinhalt beibehalten wurde, ruft der Host die `IPersist*::Load`\-Methode des Skriptmoduls auf, um dem Skriptspeicher, \-Stream oder \-Eigenschaftensammlung zu speisen.  Andernfalls verwendet der Host entweder `IPersist*::InitNew` oder [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md)\-Methode NULL, um ein Skript zu erstellen.  Ein Host, der ein Skript beibehält, während Text [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) verwenden kann, um dem Skriptmodul den Text des Skripts auf speisen, nachdem `IActiveScriptParse::InitNew` aufgerufen wurde.  
  
4.  Hinzufügen von benannten Elementen.  Für jedes genannte Element der obersten Ebene \(wie Seiten und Formulare\) importiert in den Namespace des Skriptmoduls, ruft der Host die [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md)\-Methode auf, um einen Eintrag im Namespace des Moduls zu erstellen.  Dieser Schritt ist nicht erforderlich, wenn benannte Elemente der obersten Ebene bereits Teil des dauerhaften Zustands des Skripts sind, das in Schritt 3 geladen wird.  Ein Host verwendet nicht `IActiveScript::AddNamedItem`, um Zwischenebene benannte Elemente hinzuzufügen \(wie Steuerelemente auf einer HTML\-Seite\); eher erhält das Modul indirekt Zwischenebenenelemente der obersten Ebene, indem die `ITypeInfo` und `IDispatch`\-Schnittstellen des Hosts verwendet.  
  
5.  Führen Sie das Skript aus.  Der Host wird das Modul, das Ausführen des Skripts zu starten, indem das SCRIPTSTATE\_CONNECTED\-Flag [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) in der \- Methode festgelegt werden.  Dieser Aufruf wird wahrscheinlich jede Skriptmodulbauarbeit, einschließlich der statische \- Bindung ausführen, verknüpfen könnte von an Ereignisse \(siehe unten\), und führt Code, auf eine Weise aus, die einer vorbereiteten `main()`\-Funktion ähnelt.  
  
6.  Rufen Sie Elementinformationen ab.  Immer wenn das Skriptmodul ein Symbol mit einer ersten Seite eines Dokuments zugeordnet werden muss, wird die [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md)\-Methode auf, die Informationen über das angegebene Element zurückgibt.  
  
7.  Einbinden von Ereignissen.  Bevor der das eigentliche Skript beginnt, schließt das Skriptmodul an die Ereignisse aller relevanten Objekte über die `IConnectionPoint`\-Schnittstelle an.  
  
8.  Rufen Sie Eigenschaften und Methoden.  Während das Skript ausgeführt wird, erkennt das Skriptmodul Verweise auf Methoden und Eigenschaften auf benannten Objekten durch `IDispatch::Invoke` oder andere Mechanismen Bindung des Standards OLE.  
  
## Windows Script\-Begriffe  
 Diese Liste enthält Definitionen der Skripterstellung\-verknüpften Begriffe, die in diesem Dokument verwendet werden.  
  
|Begriff|Definition|  
|-------------|----------------|  
|Codeobjekt|Eine Instanz erstellt durch das Skriptmodul, das mit einem benannten Element wie dem Modul, der einem Formular in Visual Basic oder eine C\+\+\-Klasse, die mit einem benannten Element zugeordnet ist zugeordnet ist.  Vorzugsweise ist dies ein \- Objekt OLE\-ComponentObject Model \(COM\), das OLE\-Automatisierung unterstützt, sodass der Host oder andere NichtSkriptentität das Codeobjekt bearbeiten können.|  
|Benanntes Element|Ein OLE\-COM\-Objekt \(vorzugsweise einen, der OLE\-Automatisierung\) unterstützt, die der Host zum Skript für interessant enthält.  Beispiele sind die HTML\-Seite und Browser in einem Webbrowser und das Dokument und die Dialogfelder in Microsoft Word.|  
|Skript|Die Daten, die das Programm bildet, das das Skriptmodul auswirkt.  Ein Skript kann alle zusammenhängenden ausführbare Daten, einschließlich Textteile, Blöcke von `pcode` oder sogar computerspezifische ausführbare Bytecodes sein.  Ein Host lädt ein Skript in das Skriptmodul durch eine der `IPersist*`\-Schnittstellen oder durch die [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)\-Schnittstelle.|  
|Skriptmodul|Das OLE\-Objekt, das Skripts verarbeitet.  Ein Skriptmodul implementiert die [IActiveScript](../winscript/reference/iactivescript.md) und optional [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)\-Schnittstellen.|  
|Skipthost|Die Anwendung oder das Programm, das die Windows Script\-Modul besitzt.  Der Host implementiert die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) und optional [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md)\-Schnittstellen.|  
|Skriptlet|Ein Teil eines Skripts, das angefügtes an ein \- Objekt durch die [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)\-Schnittstelle erhält.  Die gesamte Auflistung von Skriptlets ist das Skript.|  
|Skriptsprache|Die Sprache, in der ein Skript \(VBScript\), und die Semantik dieser Sprache geschrieben ist.|  
  
## Siehe auch  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)