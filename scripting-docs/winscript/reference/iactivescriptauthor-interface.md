---
title: IActiveScriptAuthor-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645770"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor-Schnittstelle
Stellt die Erstellung von Diensten, einschließlich IntelliSense und die Sortierung der Informationen dar.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptAuthor` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Fügt den Namen eines Elements auf der Stammebene an das Skript des Moduls Namespace erstellen. Ein *Element auf der Stammebene* ist ein Objekt, das Eigenschaften und Methoden enthalten kann, und eine Ereignisquelle enthalten können.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Fügt einen Code-Scriptlet als ein untergeordnetes Element der Stammebene `IScriptNode` Objekt. Der vollqualifizierte Name des Scriptlets kann nur zwei Ebenen verfügen, auf dem Host.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Der Namespace für das Skript wird eine Typbibliothek hinzugefügt.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Gibt den Satz der Abschluss Zeichen für einen Kontext für die angeforderte Abschluss.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Gibt das Scriptlet, das die angegebenen Attribute aufweist.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Gibt geben Informationen und Anker Positionen für ein angegebenes Zeichen in einem Code-Block. Dies bietet Informationen für Member, IntelliSense, globalen Listen und parametertipps.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Gibt Informationen zurück.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Gibt die `IScriptNode` Stamm des Autors Skript-Struktur.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Gibt den Textattribute des Scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Gibt die Textattribute eines Skriptblocks.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Gibt einen Wert, der angibt, ob ein angegebenes Zeichen eine Anweisungsvervollständigung von der Anwendung festlegen sollten.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Skripttext analysiert und fügt Text an das authoring Skript authoring Modul erstellt eine `IScriptEntry` Objekt, das den Skriptblock entspricht.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Entfernt eine `NamedItem` Objekt aus dem Namespace des Skripts Modul erstellen.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Entfernt eine Typbibliothek aus dem Skript Modul Namespace erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)