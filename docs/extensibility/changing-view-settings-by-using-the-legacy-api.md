---
title: Ändern von Einstellungen mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc0dc26a01cdddb4b26dfa65acab2c497618a76e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926896"
---
# <a name="change-view-settings-by-using-the-legacy-api"></a>Ändern der ansichtseinstellungen mithilfe der legacy-API
Einstellungen, die Kern-Editor-Features, z. B. Zeilenumbruch, Auswahlrand und virtuellen Leerraum befindet, können geändert werden, durch den Benutzer von der **Optionen** Dialogfeld. Es ist jedoch auch möglich, zum Ändern dieser Einstellungen programmgesteuert.

## <a name="change-settings-by-using-the-legacy-api"></a>Ändern von Einstellungen mithilfe der legacy-API
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle verfügbar macht, einen Satz von Eigenschaften für Text-Editor. Die Textansicht enthält eine Kategorie von Eigenschaften (GUID_EditPropCategory_View_MasterSettings), die die Gruppe der programmgesteuert geänderte Einstellungen für die Textansicht darstellt. Sobald auf diese Weise Einstellungen geändert wurden, sie können nicht geändert werden, der **Optionen** (Dialogfeld), bis sie zurückgesetzt werden.

 Es folgt der typische Prozess zum Ändern der Einstellungen für eine Instanz von der Kern-Editor anzeigen.

1. Rufen Sie `QueryInterface` auf die (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle.

2. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> -Methode, geben Sie einen Wert GUID_EditPropCategory_View_MasterSettings für die `rguidCategory` Parameter.

     Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> -Schnittstelle, die den Satz der erzwungenen Eigenschaften für die Sicht enthält. Alle Einstellungen in dieser Gruppe werden dauerhaft erzwungen. Wenn eine Einstellung nicht in dieser Gruppe vorhanden ist, wird es im angegebenen Optionen folgen der **Optionen** Dialogfeld oder die Befehle des Benutzers.

3. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Methode, und geben den Wert der entsprechenden Einstellungen in der `idprop` Parameter.

     Beispielsweise um Zeilenumbruch zu erzwingen, rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> und geben Sie den Wert VSEDITPROPID_ViewLangOpt_WordWrap, `vt` für die `idprop` Parameter. In diesem Aufruf `vt` ist eine Variante des Typs VT_BOOL und `vt.boolVal` auf VARIANT_TRUE festgelegt ist.

## <a name="reset-changed-view-settings"></a>Einstellungen zurücksetzen geändert
 Rufen Sie zum Zurücksetzen einer beliebigen geänderten Ansicht, die für eine Instanz von der Kern-Editor Festlegen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> Methode, und geben Sie den Wert der entsprechenden Einstellung in der `idprop` Parameter.

 Z. B. um Zeilenumbruch schweben zu ermöglichen, Sie würden es aus der Eigenschaftskategorie entfernen durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> und geben Sie einen Wert VSEDITPROPID_ViewLangOpt_WordWrap für die `idprop` Parameter.

 Um alle geänderten Einstellungen für die Kern-Editor auf einmal zu entfernen, geben Sie den Wert VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt für die `idprop` Parameter. Klicken Sie in diesem Aufruf vt ist eine Variante des Typs VT_BOOL und vt.boolVal ist auf VARIANT_TRUE festgelegt.

## <a name="see-also"></a>Siehe auch
- [In der Kern-editor](../extensibility/inside-the-core-editor.md)
- [Access TheText-Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
- [Optionen (Dialogfeld)](../ide/reference/options-dialog-box-visual-studio.md)