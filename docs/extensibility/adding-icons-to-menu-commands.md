---
title: "Hinzufügen von Symbolen zu Menübefehlen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 06d90b5174cc9ff2d09d7ccba8b2f39bc1d2a077
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-icons-to-menu-commands"></a>Hinzufügen von Symbolen zu Menübefehlen
Befehle können in Menüs oder Symbolleisten angezeigt werden. Auf der Symbolleiste wird häufig für einen Befehl mit nur einem Symbol (um Platz zu sparen) beim in Menüs angezeigt werden, dass ein Befehl in der Regel mit einem Symbol und der Text angezeigt.  
  
 Symbole sind 16 Pixel breit und 16 Pixel hoch und eine 8-Bit-Farbtiefe (256 Farben) oder 32-Bit-Farbtiefe ("true" Farbe). 32-Bit-Farbsymbole werden bevorzugt. Symbole sind normalerweise in einer einzelnen horizontalen Reihe in eine einzelne Bitmap angeordnet, obwohl mehrere Bitmaps zulässig sind. Diese Bitmap wird in der VSCT-Datei zusammen mit die einzelnen Symbole in der Bitmap verfügbar deklariert. Finden Sie in der Referenz für die [Bitmaps Element](../extensibility/bitmaps-element.md) Weitere Details.  
  
## <a name="adding-an-icon-to-a-command"></a>Ein Symbol hinzufügen für einen Befehl  
 Das folgende Verfahren wird davon ausgegangen, dass Sie ein vorhandenes VSPackage-Projekt mit einem Menübefehl verfügen. Informationen hierzu finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Erstellen Sie eine Bitmap mit einer Farbtiefe von 32-Bit. Ein Symbol ist immer 16 x 16, sodass diese Bitmap 16 Pixel hoch sein muss und ein Vielfaches von 16 Pixel breit.  
  
     Jedes Symbol wird auf die Bitmap nebeneinander in einer einzelnen Zeile platziert. Verwenden Sie den alpha-Kanal, um Positionen in der Transparenz in jedes Symbol anzuzeigen.  
  
     Wenn Sie eine 8-Bit-Farbtiefe verwenden, verwenden Sie Magenta `RGB(255,0,255)`, als die Transparenz. Allerdings werden die 32-Bit-Farbsymbole bevorzugt.  
  
2.  Kopieren Sie die Symboldatei, zu dem Verzeichnis "Resources" in Ihrem VSPackage-Projekt. Fügen Sie im Projektmappen-Explorer das Symbol zum Projekt hinzu. (Wählen Sie Ressourcen aus, und klicken Sie im Kontextmenü auf Hinzufügen, und klicken Sie dann auf Vorhandenes Element, und wählen Sie die Symboldatei.)  
  
3.  Öffnen Sie die VSCT-Datei im Editor.  
  
4.  Hinzufügen einer `GuidSymbol` Element mit dem Namen **TestIcon**. Erstellen Sie eine GUID (**Extras / erstellen GUID**, und wählen Sie dann **Registrierungsformat** , und klicken Sie auf Kopieren), und fügen Sie ihn in die `value` Attribut. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Hinzufügen einer `<IDSymbol>` für das Symbol. Die `name` Attribut ist das Symbol-ID und die `value` seiner Position auf der Leiste zeigt an, sofern vorhanden. Wenn nur ein Symbol vorhanden ist, fügen Sie 1 hinzu. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Erstellen einer `<Bitmap>` in die `<Bitmaps>` Abschnitt der VSCT-Datei zum Darstellen der Bitmap, die die Symbole enthält.  
  
    -   Legen Sie die `guid` Wert, der den Namen des der `<GuidSymbol>` Element, die Sie im vorherigen Schritt erstellt haben.  
  
    -   Legen Sie die `href` Wert, der den relativen Pfad der Bitmapdatei mithilfe einer (in diesem Fall **Ressourcen\\< Dateiname des Symbols\>**.  
  
    -   Legen Sie die `usedList` Wert, der die IDSymbol, die Sie zuvor erstellt haben. Dieses Attribut gibt eine durch Trennzeichen getrennte Liste der Symbole im VSPackage verwendet werden. Ausgeschlossene Formularkompilierung werden die Symbole nicht in der Liste.  
  
         Die Bitmap-Block sollte wie folgt aussehen:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  In der vorhandenen `<Button>` -Elementgruppe, die `Icon` Element auf die GUIDSymbol und IDSymbol-Werte, die Sie zuvor erstellt haben. Hier ist ein Beispiel für ein Button-Element mit diesen Werten:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Testen Sie das Symbol. Erstellen Sie das Projekt, und starten Sie das Debugging. Suchen Sie in der experimentellen Instanz den Befehl ein. Es sollte dem Symbol angezeigt werden, dass Sie hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [VSCT-XML-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)