---
title: IActiveScriptAuthor-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b3d9725d72f5213aadc3d9400bef87cecb20ba0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009728"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor-Schnittstelle
Stellt das Erstellen von Diensten, einschließlich IntelliSense und die Sortierung der Informationen dar.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptAuthor` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Fügt den Namen eines Elements auf der Stammebene an das Skript-Engine-Namespace erstellen. Ein *auf Stammebene Element* ist ein Objekt, das Eigenschaften und Methoden enthalten kann, und eine Ereignisquelle enthalten können.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Fügt einen Code-Scriptlet als untergeordnetes Element der Stammebene `IScriptNode` Objekt. Im Host haben der vollqualifizierte Namen des Scriptlets nur zwei Ebenen.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Der Namespace für das Skript wird eine Typbibliothek hinzugefügt.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Gibt den Satz der Abschluss Zeichen für einen Kontext für die angeforderte Abschluss.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Gibt zurück, das Scriptlet, das die angegebenen Attribute aufweist.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Gibt geben Informationen und Positionen der Anker für ein angegebenes Zeichen in einem Codeblock. Dies bietet Informationen für Mitglied, IntelliSense, globale Listen und parametertipps.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Gibt die Language-Informationen zurück.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Gibt die `IScriptNode` Stamm des Autors-Skript-Struktur.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Gibt den Textattribute des Scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Gibt die Textattribute eines Skriptblocks.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Gibt einen Wert, der angibt, ob ein angegebenes Zeichen von der Anwendung eine Anweisungsvervollständigung committet werden soll.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Skripttext analysiert und fügt den Text für das authoring Skript-Engine-Erstellung erstellt eine `IScriptEntry` Objekt, das den Skriptblock entspricht.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Entfernt eine `NamedItem` Objekt aus dem Namespace, der das Skript-Engine-Erstellung.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Entfernt eine Typbibliothek aus dem Skript-Engine-Namespace erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)