---
title: "Gewusst wie: Hinzuf&#252;gen von Befehlen zu Kontextmen&#252;s | Microsoft Docs"
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
  - "Office-Menüs, erstellen"
  - "Office-Entwicklung in Visual Studio, Kontextmenüs"
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: Hinzuf&#252;gen von Befehlen zu Kontextmen&#252;s
  In diesem Thema wird veranschaulicht, wie ein VSTO\-Add\-In verwendet werden kann, um einem Kontextmenü in einer Office\-Anwendung Befehle hinzuzufügen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### So fügen Sie in Office einem Kontextmenü Befehle hinzu  
  
1.  Fügen Sie ein **Menüband\-XML**\-Element einem Projekt auf Dokumentebene oder einem VSTO\-Add\-In\-Projekt hinzu. Weitere Informationen finden Sie unter [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md). In  
  
2.  **Projektmappen\-Explorer** wählen Sie **ThisAddIn.cs** oder **ThisAddIn.vb** aus.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** und **Code** aus.  
  
     Die **ThisAddin**\-Klassendatei wird im Code\-Editor geöffnet.  
  
4.  Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Mit diesem Code wird die CreateRibbonExtensibilityObject\-Methode überschrieben und der Office\-Anwendung die Menüband\-XML\-Klasse zurückgegeben.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#1)]  
  
5.  Wählen Sie die Menüband\-XML\-Datei im **Projektmappen\-Explorer** aus. Standardmäßig erhält die Menüband\-XML\-Datei den Namen "Ribbon1.xml".  
  
6.  Wählen Sie in der Menüleiste **Ansicht** und **Code** aus.  
  
     Die Menüband\-XML\-Datei wird im Code\-Editor geöffnet.  
  
7.  Fügen Sie im Code\-Editor den XML\-Code hinzu, der das Kontextmenü und das Steuerelement beschreibt, das Sie dem Kontextmenü hinzufügen möchten.  
  
     Im folgenden Beispiel werden dem Kontextmenü für ein Word\-Dokument ein Schaltflächen\-, ein Menü\- und ein Katalog\-Steuerelement hinzugefügt. Die Steuerelement\-ID dieses Kontextmenüs lautet „ContextMenuText“. Eine vollständige Liste der Steuerelement\-IDs für Office 2010\-Kontextmenüs finden Sie unter [Office 2010 Help Files: Office Fluent User Interface Control Identifiers](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui"> <contextMenus> <contextMenu idMso="ContextMenuText"> <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" /> <menu id="MySubMenu" label="My Submenu" > <button id="MyButton2" label="Button on submenu" /> </menu> <gallery id="galleryOne" label="My Gallery"> <item id="item1" imageMso="HappyFace" /> <item id="item2" imageMso="HappyFace" /> <item id="item3" imageMso="HappyFace" /> <item id="item4" imageMso="HappyFace" /> </gallery> </contextMenu> </contextMenus> </customUI>  
    ```  
  
8.  Wählen Sie im **Projektmappen\-Explorer** die Datei **MyRibbon.cs** oder **MyRibbon.vb** aus.  
  
9. Fügen Sie der `Ribbon1`\-Klasse eine Rückrufmethode für jedes Steuerelement hinzu, das Sie verarbeiten möchten.  
  
     Die folgende Rückrufmethode verarbeitet die Schaltfläche **My Button**. In diesem Code wird dem aktiven Dokument an der aktuellen Position des Cursors eine Zeichenfolge hinzugefügt.  
  
     [!code-csharp[Trin_WordAddIn_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/ribbon1.cs#2)]
     [!code-vb[Trin_WordAddIn_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/ribbon1.vb#2)]  
  
## Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Anpassen von Kontextmenüs in Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  