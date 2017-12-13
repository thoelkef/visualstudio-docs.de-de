---
title: Windows-Skriptschnittstellen | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200a1ac1bf273e2515e1e17b6f83c2020ff9884d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-interfaces"></a>Windows-Skriptschnittstellen
Microsoft Windows-Skriptschnittstellen ermöglichen es Anwendungen, Skripterstellung und OLE-Automatisierung hinzuzufügen. Skript-Hosts, die von Windows Script abhängig sind, können Skriptmodule aus mehreren Quellen und von mehreren Herstellern nutzen, um die Skripterstellung zwischen Komponenten zu verwalten. Die Implementierung des Skripts an sich – Sprache, Syntax, persistentes Format, Ausführungsmodell, usw. – obliegt dem Skripthersteller.  
  
 Die Windows Script-Dokumentation ist in folgende Abschnitte unterteilt:  
  
 [Windows Script Hosts](../winscript/windows-script-hosts.md)  
  
 [Windows Script-Module](../winscript/windows-script-engines.md)  
  
 [Debuggen mit Active Script – Übersicht](../winscript/active-script-debugging-overview.md)  
  
 [Active Script-Profilerstellung – Übersicht](../winscript/active-script-profiling-overview.md)  
  
 [Windows Script-Schnittstellenreferenz](../winscript/reference/windows-script-interfaces-reference.md)  
  
## <a name="windows-script-background"></a>Hintergrund von Windows Script  
 Windows Script-Schnittstellen können zwei Kategorien zugeordnet werden: Windows Script Hosts und Windows Script-Module. Ein Host erstellt ein Skriptmodul und ruft das Modul dazu auf, die Skripts auszuführen. Beispiele für Windows Script Hosts:  
  
-   Microsoft Internet Explorer  
  
-   Internet-Dokumenterstellungstools  
  
-   Shell  
  
 Windows Script-Module können für sämtliche Sprach- oder Laufzeitumgebungen entwickelt werden, einschließlich:  
  
-   Microsoft Visual Basic Scripting Edition (VBScript)  
  
-   Perl  
  
-   Lisp  
  
 Für Windows Script steht ein Wrapper für die OLE-Automatisierung zur Verfügung, damit die Implementierung des Hosts so flexibel wie möglich gestaltet werden kann. Allerdings besitzt ein Host, der mithilfe dieses Wrapperobjekts das Skriptmodul instanziiert, weniger Kontrolle über den Laufzeit-Namespace, das Persistenzmodell, usw. als beim direkten Verwenden von Windows Script.  
  
 Windows Script wurde so designt, dass die Elemente der Benutzeroberfläche ausgelagert sind, die nur in einer Erstellungsumgebung erforderlich sind. Somit können Hosts (z.B. Browser und Viewer) und Skriptmodule (z.B. VBScript), die nicht am Erstellen beteiligt sind, schlank gehalten werden.  
  
## <a name="windows-script-basic-architecture"></a>Basisarchitektur von Windows Script  
 Die folgende Abbildung zeigt die Interaktion zwischen einem Windows Script Host und einem Windows Script-Modul.  
  
 In der folgenden Liste sind die Schritte, die Teil der Interaktion zwischen Host und Modul sind, angegeben.  
  
1.  Erstellen eines Projekts. Der Host lädt ein Projekt oder ein Dokument. (Dieser Schritt ist für Windows Script nicht relevant, aber aus Gründen der Vollständigkeit hier aufgeführt.)  
  
2.  Erstellen des Windows Script-Moduls. Der Host ruft `CoCreateInstance` auf, um ein neues Windows Script-Modul zu erstellen. Dabei gibt er den Klassenbezeichner (CLSID) des zu verwendenden bestimmten Skriptmoduls an. Beispielsweise empfängt der HTML-Browser des Internet Explorers den Klassenbezeichner des Skriptmoduls über das Attribut CLSID= des HTML-Tags \<OBJECT>.  
  
3.  Laden des Skripts. Wenn die Skriptinhalte beibehalten wurden, ruft der Host die `IPersist*::Load`-Methode des Skriptmoduls auf, um ihm den Behälter zur Speicherung des Skripts, den Datenstrombehälter oder den Eigenschaftenbehälter zuzuführen. Andernfalls verwendet der Host entweder die `IPersist*::InitNew`-Methode oder die [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md)-Methode, um ein Skript mit dem Wert NULL zu erstellen. Ein Host, der ein Skript in Textform verwaltet, kann mithilfe von [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) dem Skripttext das Skriptmodul zuführen, nachdem er zuvor `IActiveScriptParse::InitNew` aufgerufen hat.  
  
4.  Hinzufügen benannter Elemente. Für jedes benannte Element der obersten Ebene (z.B. Seiten und Formulare), das in den Skriptmodul-Namespace importiert wurde, ruft der Host die [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md)-Methode auf, um im Namespace des Moduls einen Eintrag zu erstellen. Dieser Schritt ist nicht erforderlich, wenn die benannten Elemente der obersten Ebene bereits Teil des persistenten Status jenes Skripts sind, das in Schritt 3 geladen wurde. Ein Host verwendet nicht die Methode `IActiveScript::AddNamedItem`, um benannte Elemente der unteren Ebene (z.B. Steuerelemente auf einer HTML-Seite) hinzuzufügen; stattdessen ruft das Modul Elemente der unteren Ebene indirekt über Elemente aus der obersten Ebene ab, indem es die Hostschnittstellen `ITypeInfo` und `IDispatch` nutzt.  
  
5.  Ausführen des Skripts. Der Host bringt das Modul dazu, das Skript auszuführen, indem er in der [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md)-Methode das Flag „SCRIPTSTATE_CONNECTED“ festlegt. So ähnlich wie mit einer skriptbasierten `main()`-Funktion könnte mit diesem Aufruf vermutlich jegliche Form von Konstruktionsarbeit eines Skriptmoduls durchgeführt werden, einschließlich statischer Bindung, Einbinden mit Ereignissen (siehe unten) und Ausführen von Code.  
  
6.  Abrufen von Elementinformationen. Jedes Mal, wenn das Skriptmodul einem Element der obersten Ebene ein Symbol zuordnen muss, ruft es die [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md)-Methode auf, die daraufhin Informationen über das Element zurückgibt.  
  
7.  Einbinden mit Ereignissen. Bevor Sie das eigentliche Skript starten, stellt das Skriptmodul über die `IConnectionPoint`-Schnittstelle eine Verbindung zu den Ereignissen aller relevanten Objekte her.  
  
8.  Aufrufen von Eigenschaften und Methoden. Während das Skript ausgeführt wird, erstellt das Skriptmodul bei benannten Objekten mithilfe von `IDispatch::Invoke` oder anderen Standardmechanismen der OLE-Bindung Verweise auf Methoden und Eigenschaften.  
  
## <a name="windows-script-terms"></a>Windows Script-Begriffe  
 Diese Liste enthält die Definitionen der in diesem Dokument verwendeten Begriffe im Zusammenhang mit Skripterstellung.  
  
|Begriff|Definition|  
|----------|----------------|  
|Codeobjekt|Eine Instanz, die von dem Skriptmodul erstellt wurde, das einem benannten Element zugeordnet ist, z.B. dem Modul für ein Formular in Visual Basic, oder von einer C++-Klasse, die einem benannten Element zugeordnet ist. Idealerweise ist dies ein OLE-COM-Objekt (Component Object Model), das OLE-Automatisierung unterstützt, damit der Host bzw. eine andere Entität (kein Skript) das Codeobjekt bearbeiten kann.|  
|Benanntes Element|Ein OLE-COM-Objekt (vorzugsweise OLE-Automatisierung unterstützend), von dem der Host annimmt, dass das Skript dieses verwenden könnte. Beispiele dafür sind die HTML-Seite und der -Browser in einem Webbrowser sowie die Dokumente und Dialogfelder in Microsoft Word.|  
|Skript|Die Daten, aus denen das Programm besteht, das durch das Skriptmodul ausgeführt wird. Ein Skript kann aus zusammenhängenden, ausführbaren Daten jeglicher Art bestehen, einschließlich Textelementen, `pcode`-Blöcken oder sogar ausführbaren, computerspezifischen Bytecodes. Ein Host lädt ein Skript über eine der `IPersist*`-Schnittstellen oder über die [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)-Schnittstelle in das Skriptmodul.|  
|Skriptmodul|Das OLE-Objekt, das Skripts verarbeitet. Ein Skriptmodul implementiert die Schnittstelle [IActiveScript](../winscript/reference/iactivescript.md) und, bei Bedarf, die Schnittstelle [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Scripting-Host|Die Anwendung oder das Programm, das das Windows Script-Modul besitzt. Der Host implementiert die Schnittstelle [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) und, bei Bedarf, die Schnittstelle [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md).|  
|Scriptlet|Teil eines Skripts, das über die [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)-Schnittstelle an ein Objekt angefügt wird. Die aggregierte Auflistung von Scriptlets nennt man Skript.|  
|Skriptsprache|Die Sprache, in der ein Skript geschrieben ist (z.B. VBScript), und die Semantik jener Sprache.|  
  
## <a name="see-also"></a>Siehe auch  
 [Windows-Skriptschnittstellen](../winscript/windows-script-interfaces.md)