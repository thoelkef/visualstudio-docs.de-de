---
title: Ändern von Einstellungen mithilfe der Legacy-API | Microsoft-Dokumentation
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
ms.openlocfilehash: ddca5f9159c2cb20eeb8525bd37730a88f64fb43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957985"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Ändern von Einstellungen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einstellungen, die Kern-Editor-Features, z. B. Zeilenumbruch, Auswahlrand und virtuellen Leerraum befindet, können geändert werden, durch den Benutzer von der **Optionen** Dialogfeld. Es ist jedoch auch möglich, zum Ändern dieser Einstellungen programmgesteuert.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Ändern von Einstellungen mithilfe der Legacy-API  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle verfügbar macht, einen Satz von Eigenschaften für Text-Editor. Die Textansicht enthält eine Kategorie von Eigenschaften (GUID_EditPropCategory_View_MasterSettings), die die Gruppe der programmgesteuert geänderte Einstellungen für die Textansicht darstellt. Sobald auf diese Weise Einstellungen geändert wurden, sie können nicht geändert werden, der **Optionen** (Dialogfeld), bis sie zurückgesetzt werden.  
  
 Es folgt der typische Prozess zum Ändern der Einstellungen für eine Instanz von der Kern-Editor anzeigen.  
  
1.  Rufen Sie `QueryInterface` auf die (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Schnittstelle.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> -Methode, geben Sie einen Wert GUID_EditPropCategory_View_MasterSettings für die `rguidCategory` Parameter.  
  
     Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> -Schnittstelle, die den Satz der erzwungenen Eigenschaften für die Sicht enthält. Alle Einstellungen in dieser Gruppe werden dauerhaft erzwungen. Wenn eine Einstellung nicht in dieser Gruppe vorhanden ist, wird es im angegebenen Optionen folgen der **Optionen** Dialogfeld oder die Befehle des Benutzers.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Methode, und geben den Wert der entsprechenden Einstellungen in der `idprop` Parameter.  
  
     Beispielsweise um Zeilenumbruch zu erzwingen, rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> und geben Sie den Wert VSEDITPROPID_ViewLangOpt_WordWrap, `vt` für die `idprop` Parameter. In diesem Aufruf `vt` ist eine Variante des Typs VT_BOOL und `vt.boolVal` auf VARIANT_TRUE festgelegt ist.  
  
## <a name="resetting-changed-view-settings"></a>Von geänderten Anzeigeeinstellungen werden zurückgesetzt  
 Rufen Sie zum Zurücksetzen einer beliebigen geänderten Ansicht, die für eine Instanz von der Kern-Editor Festlegen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> Methode, und geben Sie den Wert der entsprechenden Einstellung in der `idprop` Parameter.  
  
 Z. B. um Zeilenumbruch schweben zu ermöglichen, Sie würden es aus der Eigenschaftskategorie entfernen durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> und geben Sie einen Wert VSEDITPROPID_ViewLangOpt_WordWrap für die `idprop` Parameter.  
  
 Um alle geänderten Einstellungen für die Kern-Editor auf einmal zu entfernen, geben Sie den Wert VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt für die `idprop` Parameter. Klicken Sie in diesem Aufruf vt ist eine Variante des Typs VT_BOOL und vt.boolVal ist auf VARIANT_TRUE festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [In der Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Zugreifen auf TheText Ansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Optionen (Dialogfeld)](../ide/reference/options-dialog-box-visual-studio.md)
