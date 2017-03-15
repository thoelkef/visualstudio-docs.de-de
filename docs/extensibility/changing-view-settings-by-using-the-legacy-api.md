---
title: "&#196;ndern die Ansicht mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - ändern die Ansicht"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# &#196;ndern die Ansicht mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Einstellungen für Kern des Editors, wie Zeilenumbruch, Auswahlrand Virtuellen Bereich und können vom Benutzer mithilfe des Dialogfelds **Optionen** geändert werden.  Es ist jedoch auch möglich, diese Einstellungen programmgesteuert ändern.  
  
## Einstellungen mithilfe des Legacy API ändern  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>\-Schnittstelle macht einen Satz Text\-Editor\-Eigenschaften.  Die Textansicht enthält eine Kategorie Properties \(GUID\_EditPropCategory\_View\_MasterSettings\), die die Gruppe von programmgesteuert geänderten Einstellungen für die Textansicht darstellt.  Sobald die Ansicht sind auf diese Weise sie können nicht geändert werden **Optionen** im Dialogfeld geändert wurde, bis sie zurückgesetzt werden.  
  
 Im Folgenden ist der übliche Verfahren zum Ändern von Einstellungen anzeigen für eine Instanz des zentralen editors.  
  
1.  Rufen Sie `QueryInterface` \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>\-Schnittstelle an.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>\-Methode auf und einen Wert von GUID\_EditPropCategory\_View\_MasterSettings für den `rguidCategory`\-Parameter angeben.  
  
     Dies gibt einen Zeiger auf die zu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>\-Schnittstelle zurück, die den Satz der erzwungenen Eigenschaften für die Sicht enthält.  Einstellungen in dieser Gruppe werden dauerhaft erzwungen.  Wenn eine Einstellung nicht in dieser Gruppe ist, dann folgt sie den Optionen, die im **Optionen** Dialogfeld oder in Befehlen des Benutzers angegeben werden.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>\-Methode auf und den entsprechenden Wert für die Einstellung im `idprop`\-Parameter angeben.  
  
     Zum Beispiel verwendet und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Aufrufs, Zeilenumbruch einen Wert VSEDITPROPID\_ViewLangOpt\_WordWrap, `vt` angeben `idprop` für den Parameter.  In diesem Aufruf ist `vt` VARIANT des Typs VT\_BOOL und `vt.boolVal` ist VARIANT\_TRUE sein.  
  
## Geänderte Ansichts\-Einstellungen zurücksetzen  
 So erstellen Sie eine geänderte Einstellung für die Ansicht für eine Instanz des zentralen editors zurücksetzen, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>\-Methode aufrufen und den entsprechenden Einstellungswert im `idprop`\-Parameter angeben.  
  
 Um beispielsweise Zeilenumbrüche zu ermöglichen, frei zu schwimmen, können Sie ihn von der Eigenschaft durch den Aufruf von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> Kategorie und das Angeben eines Werts aus VSEDITPROPID\_ViewLangOpt\_WordWrap für den Parameter `idprop` entfernen.  
  
 Um alle geänderten Einstellungen für den Kern des Editors gleichzeitig zu entfernen, geben Sie einen Wert von VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults, vt für den `idprop`\-Parameter an.  In diesem Aufruf ist vt VARIANT des Typs VT\_BOOL und vt.boolVal ist VARIANT\_TRUE sein.  
  
## Siehe auch  
 [In der Core\-Editor](../extensibility/inside-the-core-editor.md)   
 [Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Dialogfeld "Optionen"](../ide/reference/options-dialog-box-visual-studio.md)