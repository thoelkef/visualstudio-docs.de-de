---
title: "Barrierefreiheit in Office-Projekten | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Barrierefreiheit [Office-Entwicklung in Visual Studio]"
  - "Office-Entwicklung in Visual Studio, Barrierefreiheit"
  - "Menüband [Office-Entwicklung in Visual Studio], Tastenkombinationen"
  - "Tastenkombinationen [Office-Entwicklung in Visual Studio]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Barrierefreiheit in Office-Projekten
  Microsoft Visual Studio und Microsoft Office verfügen über viele Barrierefreiheitsfeatures, mit denen Sie benutzerdefinierte Projektmappen gemäß den Standardanforderungen für Barrierefreiheit erstellen können.  Microsoft veröffentlicht Richtlinien für Barrierefreiheit im Internet.  Ausführliche Informationen finden Sie auf der [Accessibility\-Website](http://go.microsoft.com/fwlink/?LinkID=37113).  
  
 In den meisten Fällen entsprechen Office\-Projekte in Visual Studio den Standards für Barrierefreiheit, oder es werden Eigenschaften zur Verfügung gestellt, mit denen Sie Projektmappen barrierefrei gestalten können.  Aber es gibt einige Features, die nur eingeschränkt barrierefrei sind.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Barrierefreiheit zur Entwurfszeit  
  
### Verwenden von Tastenkombinationen in Projekten auf Dokumentebene  
 Wenn ein Microsoft Office Word\-Dokument bzw. eine Microsoft Office Excel\-Arbeitsmappe in Visual Studio geöffnet wird, erhält jeweils nur eine Anwendung den Befehl der Tastenkombination.  Standardmäßig empfängt Visual Studio alle Befehle der Tastenkombination. Doch Sie können festlegen, dass die Befehle an Word bzw. Excel gesendet werden, wenn das Dokument den Fokus besitzt. Wählen Sie dazu im Dialogfeld **Optionen** auf der Seite **Tastatureinstellungen** die Option **Dynamisches Tastaturschema** aus.  Weitere Informationen finden Sie unter [Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) und [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### Anzeigen von Tastenkombinationen für das Menüband in Projekten auf Dokumentebene  
 Wenn ein Word\-Dokument bzw. eine Excel\-Arbeitsmappe in Visual Studio geöffnet ist, können Sie durch Drücken der ALT\-TASTE keine Tastenkombinationen für die Registerkarten und Steuerelemente auf dem Menüband anzeigen.  Um die Tastenkombinationen anzuzeigen, während das Dokument bzw. die Arbeitsmappe im Designer geöffnet ist, führen Sie die folgenden Schritte aus.  
  
##### So zeigen Sie Tastenkombinationen für Registerkarten und Steuerelemente auf dem Menüband im Designer an  
  
1.  Klicken Sie in Visual Studio im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie den Knoten **Office\-Tools**, und wählen Sie je nach Bedarf **Microsoft Office Excel\-Tastatur** bzw. **Microsoft Office Word\-Tastatur** aus.  
  
3.  Wählen Sie **Dynamisches Tastaturschema** aus.  
  
     Es wird eine Meldung mit dem Hinweis angezeigt, dass Sie Visual Studio neu starten müssen, damit die Änderung wirksam wird.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie Visual Studio neu, und öffnen Sie das Projekt erneut.  
  
6.  Öffnen Sie den Dokument\- bzw. Arbeitsmappen\-Designer für das Projekt.  
  
7.  Drücken Sie F6, um die Tastenkombinationen für das Menüband anzuzeigen.  
  
## Barrierefreiheit zur Laufzeit  
  
### Windows Forms\-Steuerelemente in Office\-Dokumenten  
 Windows Forms\-Steuerelemente machen Barrierefreiheitseigenschaften verfügbar, sodass Barrierefreiheit\-Hilfsmittel, z. B. die Bildschirmsprachausgabe, Informationen über das Steuerelement abrufen können.  Wenn sich die Steuerelemente in einem Office\-Dokument in einer Anpassung auf Dokumentebene befinden, können Sie diese Barrierefreiheitseigenschaften nutzen.  Weitere Informationen finden Sie unter [Informationen über Eingabehilfen für Steuerelemente in Windows Forms](http://msdn.microsoft.com/library/887dee6f-5059-4d57-957d-7c6fcd4acb10).  
  
 Allerdings gibt es zur Laufzeit einige Einschränkungen der Barrierefreiheit, wenn Windows Forms\-Steuerelemente in einer Excel\-Arbeitsmappe bzw. einem Word\-Dokument gehostet werden:  
  
-   Sie können nicht mithilfe der TAB\-TASTE von einem Steuerelement zum anderen springen.  
  
-   Wenn die Zoomeinstellung nicht auf 100% festgelegt ist, sind die Steuerelemente auf dem Dokument deaktiviert.  
  
 Informationen zu Einschränkungen bei Windows Forms\-Steuerelementen auf Dokumenten finden Sie unter [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### Aktionsbereiche und benutzerdefinierte Aufgabenbereiche  
 Wenn ein Aktionsbereich bzw. ein benutzerdefinierter Aufgabenbereich den Fokus hat, greifen Sie auf die Steuerelemente genauso zu wie auf die Steuerelemente einer Windows Forms\-Anwendung.  Um mit dem Cursor zwischen dem Aktionsbereich und dem Dokument zu wechseln, können Sie **F6** drücken.  
  
 Weitere Informationen über Aktionsbereiche und benutzerdefinierte Aufgabenbereiche finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md) und unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
### Anzeigemodi  
 Visual Studio besitzt bezüglich der Anzeigemodi folgende Einschränkungen:  
  
-   Wenn die Zoomeinstellung des Dokuments nicht auf 100% festgelegt ist, sind die Steuerelemente in einem Word\-Dokument oder in einer Excel\-Arbeitsmappe deaktiviert.  
  
-   Wenn der Benutzer die Barrierefreiheitsoption **Kontrast aktivieren** auswählt, werden die Steuerelemente im Dialogfeld **Neues Projekt** nicht ordnungsgemäß angezeigt.  
  
 Sie können diesen Einschränkungen durch die Verwendung der Bildschirmlupe begegnen.  Die Bildschirmlupe ist ein Anzeigedienstprogramm in Windows, mit dem ein Bildschirmausschnitt in einem separaten Fenster vergrößert angezeigt werden kann.  
  
## Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Barrierefreiheit für Personen mit Behinderungen](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Barrierefreiheitsfunktionen in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  