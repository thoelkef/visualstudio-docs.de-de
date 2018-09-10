---
title: 'Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9accca69c5d56461f07d21d25821c0f4181c8fbd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672673"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs
  In diesem Thema wird veranschaulicht, wie Befehle in einem Kontextmenü Menüelemente in einer Office-Anwendung hinzugefügt werden, mithilfe eines VSTO-Add-Ins.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>So fügen Sie in Office einem Kontextmenü Befehle hinzu  
  
1.  Fügen Sie ein **Menüband-XML** -Element einem Projekt auf Dokumentebene oder einem VSTO-Add-In-Projekt hinzu. Weitere Informationen finden Sie unter [wie: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md). In  
  
2.  **Projektmappen-Explorer**wählen Sie **ThisAddIn.cs** oder **ThisAddIn.vb**aus.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.  
  
     Die **ThisAddin** -Klassendatei wird im Code-Editor geöffnet.  
  
4.  Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Mit diesem Code wird die `CreateRibbonExtensibilityObject`-Methode überschrieben und der Office-Anwendung die Menüband-XML-Klasse zurückgegeben.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  Wählen Sie die Menüband-XML-Datei im **Projektmappen-Explorer**aus. In der Standardeinstellung die Menüband-XML-Datei heißt *Ribbon1.xml*.  
  
6.  Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.  
  
     Die Menüband-XML-Datei wird im Code-Editor geöffnet.  
  
7.  Fügen Sie im Code-Editor den XML-Code hinzu, der das Kontextmenü und das Steuerelement beschreibt, das Sie dem Kontextmenü hinzufügen möchten.  
  
     Im folgenden Beispiel werden dem Kontextmenü für ein Word-Dokument ein Schaltflächen-, ein Menü- und ein Katalog-Steuerelement hinzugefügt. Die Steuerelement-ID dieses Kontextmenüs lautet „ContextMenuText“. Eine vollständige Liste der Office 2010-Kontextmenü-Steuerelement IDs finden Sie unter [Office 2010-Hilfedateien: Office fluent User Interface Steuerelementbezeichnern](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  Wählen Sie im **Projektmappen-Explorer**die Datei **MyRibbon.cs** oder **MyRibbon.vb**aus.  
  
9. Fügen Sie eine Rückrufmethode, die `Ribbon1` -Klasse für jedes Steuerelement, das Sie behandeln möchten.  
  
     Die folgende Rückrufmethode verarbeitet die Schaltfläche **My Button** . In diesem Code wird dem aktiven Dokument an der aktuellen Position des Cursors eine Zeichenfolge hinzugefügt.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Anpassen von Kontextmenüs in Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  