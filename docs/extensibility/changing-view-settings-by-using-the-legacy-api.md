---
title: Ändern Einstellungen anzeigen, über die Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9857daab890c2dd7bf7a799b6dca4d1b74cb9e37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099336"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Ändern Einstellungen anzeigen, über die Legacy-API
Einstellungen für Core-Editor-Funktionen, z. B. Zeilenumbruch, Auswahlrahmen und virtuellen Adressraum können geändert werden, vom Benutzer über die **Optionen** (Dialogfeld). Es ist jedoch auch möglich, zum Ändern der Einstellungen programmgesteuert.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Ändern von Einstellungen über die Legacy-API  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle verfügbar macht, einen Satz von Eigenschaften des Text-Editor. Die Textansicht enthält eine Kategorie von Eigenschaften (GUID_EditPropCategory_View_MasterSettings), die die Gruppe der programmgesteuert geänderte Einstellungen für die Textansicht darstellt. Sobald die ansichtseinstellungen auf diese Weise geändert wurden, nicht geändert werden der **Optionen** (Dialogfeld), bis sie zurückgesetzt werden.  
  
 Es folgt der übliche Vorgang zum Ändern der Einstellungen für eine Instanz des Editors Core anzeigen.  
  
1.  Rufen Sie `QueryInterface` auf der (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> Methode, die Angabe des Werts GUID_EditPropCategory_View_MasterSettings für die `rguidCategory` Parameter.  
  
     Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> -Schnittstelle, die den Satz der erzwungenen Eigenschaften für die Sicht enthält. Alle Einstellungen in dieser Gruppe werden dauerhaft erzwungen. Wenn eine Einstellung nicht in dieser Gruppe ist, es im angegebenen Optionen befolgen wird Sie die **Optionen** Dialogfeld oder die Befehle des Benutzers.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Methode, dabei werden die entsprechenden Einstellungswert in der `idprop` Parameter.  
  
     Beispielsweise rufen Sie zum Erzwingen der Zeilenumbruch <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> und geben Sie den Wert VSEDITPROPID_ViewLangOpt_WordWrap, `vt` für die `idprop` Parameter. In diesem Aufruf `vt` ist eine Variante des Typs VT_BOOL und `vt.boolVal` auf VARIANT_TRUE festgelegt ist.  
  
## <a name="resetting-changed-view-settings"></a>Zurücksetzen des geänderten Ansichtseinstellungen  
 Aufrufen, um alle geänderten anzeigen, die Einstellung für eine Instanz des Editors Core zurückzusetzen, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> Methode, und geben Sie den Einstellungswert der entsprechenden in der `idprop` Parameter.  
  
 Beispielsweise um Zeilenumbruch schweben zu ermöglichen, möchten, entfernen sie aus "Eigenschaft" durch den Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> und dabei den Wert VSEDITPROPID_ViewLangOpt_WordWrap für die `idprop` Parameter.  
  
 Um alle geänderten Einstellungen für den Core-Editor auf einmal zu entfernen, geben Sie den Wert VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt für die `idprop` Parameter. In diesem Aufruf vt ist eine Variante des Typs VT_BOOL und vt.boolVal ist auf VARIANT_TRUE festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [In der Core-Editor](../extensibility/inside-the-core-editor.md)   
 [Zugreifen auf TheText Ansicht über die Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Optionen (Dialogfeld)](../ide/reference/options-dialog-box-visual-studio.md)