---
title: Iactivescriptauthor-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576154"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor-Schnittstelle
Stellt Erstellungs Dienste dar, einschließlich IntelliSense und der Sortierung von Informationen.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IActiveScriptAuthor`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Fügt dem Namespace der Skript Erstellungs-Engine den Namen eines Elements auf Stamm Ebene hinzu. Ein *Element* auf Stamm Ebene ist ein Objekt, das Eigenschaften und Methoden enthalten kann und auch eine Ereignis Quelle enthalten kann.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Fügt ein Code-Scriptlet als untergeordnetes Element der Stamm Ebene `IScriptNode`-Objekts hinzu. Auf dem Host kann der voll qualifizierte Name des Scriptlets nur zwei Ebenen aufweisen.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Fügt dem Namespace für das Skript eine Typbibliothek hinzu.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Gibt den Satz von Abschluss Zeichen für einen angeforderten Vervollständigungs Kontext zurück.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Gibt das Scriptlet zurück, das über die angegebenen Attribute verfügt.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Gibt Typinformationen und Anker Positionen für ein bestimmtes Zeichen in einem Codeblock zurück. Dies stellt Informationen für Member-IntelliSense, globale Listen und Parameter Tipps bereit.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Gibt Sprachinformationen zurück.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Gibt den `IScriptNode` Stamm der Skript Struktur des Autors zurück.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Gibt die Text Attribute eines Scriptlet zurück.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Gibt die Text Attribute eines Skript Blocks zurück.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Gibt einen Wert zurück, der angibt, ob ein bestimmtes Zeichen eine Anweisungs Vervollständigung durch die Anwendung übertragen soll.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analysiert Skript Text, fügt den Text der Authoring Script Authoring Engine hinzu und erstellt ein `IScriptEntry`-Objekt, das dem Skriptblock entspricht.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Entfernt ein `NamedItem` Objekt aus dem Namespace der Skript Erstellungs-Engine.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Entfernt eine Typbibliothek aus dem scriptauthoring-Engine-Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)