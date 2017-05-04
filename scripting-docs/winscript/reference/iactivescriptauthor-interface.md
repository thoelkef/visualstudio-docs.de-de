---
title: "IActiveScriptAuthor-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor-Schnittstelle"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor-Schnittstelle
Stellt Erstellungsdienste, einschließlich IntelliSense und Sortierreihenfolge von Informationen.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IActiveScriptAuthor`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Fügt den Namen eines Elements auf Stammebene den Namespace des Skripterstellungs\-Moduls hinzu.  Ein *Element auf der Stammebene* ist ein Objekt, das Eigenschaften und Methoden enthalten können und das eine Ereignisquelle auch enthalten kann.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Fügt ein Codeskriptlet als untergeordnetes Element des `IScriptNode`\-Stammebenenobjekts hinzu.  Im Host kann der vollqualifizierte Name des Skriptlets nur zwei Ebenen verfügen.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Fügt eine Typbibliothek dem Namespace für das Skript hinzu.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Gibt den Satz von Abschlusszeichen für einen angeforderten Abschlusskontext zurück.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Gibt das Skriptlet zurück, das die angegebenen Attribute verfügt.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|EINGABETASTE Typinformationen und Anchorpositionen für ein bestimmtes Zeichen in einem Codeblock.  Dies stellt Informationen für Member IntelliSense, globale Listen und Parametertipps bereit.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Gibt Sprachinformationen zurück.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Gibt den `IScriptNode` Stamm der Skriptstruktur des Autors zurück.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Gibt die Textattribute eines Skriptlets zurück.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Gibt die Textattribute eines Skriptblocks zurück.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Gibt einen Wert zurück, der angibt, ob ein bestimmtes Zeichen eine Anweisungsvervollständigung mithilfe bestätigen soll.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analysiert das Skript Text, fügen der Text dem Erstellungsskript\-Erstellungsmodul hinzu und erstellen ein `IScriptEntry`\-Objekt, das dem Skriptblock entspricht.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Entfernt ein `NamedItem`\-Objekts im Namespace des Skripterstellungsmoduls.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Entfernt eine Typbibliothek vom Skripterstellungs\-Modulnamespace.|  
  
## Siehe auch  
 [Active Script\-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)