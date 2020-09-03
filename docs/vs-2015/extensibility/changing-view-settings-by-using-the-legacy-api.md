---
title: Ändern von Ansichts Einstellungen mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184462"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Ändern von Ansichtseinstellungen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einstellungen für die Features des Kern-Editors, z. b. Zeilenumbruch, Auswahl Rand und virtueller Bereich, können vom Benutzer über das Dialogfeld **Optionen** geändert werden. Es ist jedoch auch möglich, diese Einstellungen Programm gesteuert zu ändern.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Ändern von Einstellungen mithilfe der Legacy-API  
 Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle macht einen Satz von Text-Editor-Eigenschaften verfügbar. Die Textansicht enthält eine Kategorie von Eigenschaften (GUID_EditPropCategory_View_MasterSettings), die die Gruppe der Programm gesteuert geänderten Einstellungen für die Textansicht darstellt. Nachdem die Ansichts Einstellungen auf diese Weise geändert wurden, können Sie nicht mehr im Dialogfeld **Optionen** geändert werden, bis Sie zurückgesetzt werden.  
  
 Im folgenden wird der typische Prozess zum Ändern von Ansichts Einstellungen für eine Instanz des Kern-Editors angezeigt.  
  
1. Ruft `QueryInterface` für die- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Schnittstelle () auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2. Aufrufen der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> Methode, wobei der Wert GUID_EditPropCategory_View_MasterSettings für den-Parameter angegeben wird `rguidCategory` .  
  
     Dies gibt einen Zeiger auf die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle zurück, die den Satz der erzwungenen Eigenschaften für die Sicht enthält. Alle Einstellungen in dieser Gruppe werden permanent erzwungen. Wenn sich eine Einstellung nicht in dieser Gruppe befindet, befolgt Sie die Optionen, die im Dialogfeld **Optionen** bzw. in den Befehlen des Benutzers angegeben werden.  
  
3. Aufrufen der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Methode, wobei der entsprechende Einstellungs Wert im-Parameter angegeben wird `idprop` .  
  
     Um z. b. den Zeilenumbruch zu erzwingen, müssen Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> und den Wert VSEDITPROPID_ViewLangOpt_WordWrap `vt` für den- `idprop` Parameter angeben. In diesem-Befehl `vt` ist eine Variante vom Typ VT_BOOL und `vt.boolVal` VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Geänderte Ansichts Einstellungen werden zurückgesetzt.  
 Um eine geänderte Ansichts Einstellung für eine Instanz des Kern Editors zurückzusetzen, müssen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> -Methode aufrufen und den entsprechenden Einstellungs Wert im- `idprop` Parameter angeben.  
  
 Wenn Sie z. b. den Zeilenumbruch auf freie Weise zulassen möchten, entfernen Sie ihn aus der Eigenschaften Kategorie, indem Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> und den Wert VSEDITPROPID_ViewLangOpt_WordWrap für den- `idprop` Parameter angeben.  
  
 Wenn Sie alle geänderten Einstellungen für den Kern-Editor gleichzeitig entfernen möchten, geben Sie den Wert VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT für den- `idprop` Parameter an. In diesem Befehl ist VT eine Variante vom Typ VT_BOOL und VT. boolVal ist VARIANT_TRUE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Im Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Zugreifen auf die Textansicht mithilfe der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Dialog Feld "Optionen"](../ide/reference/options-dialog-box-visual-studio.md)
