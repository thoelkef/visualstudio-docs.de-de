---
title: Hinzufügen von Symbolen zu Menübefehlen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940bef878e7360cd3709b6b3403eff2261948e0e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961241"
---
# <a name="adding-icons-to-menu-commands"></a>Hinzufügen von Symbolen zu Menübefehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Befehle können in sowohl Menüs und Symbolleisten angezeigt werden. Auf der Symbolleiste ist es üblich, dass ein Befehl aus, um mit nur einem Symbol (um Platz zu sparen) und in Menüs angezeigt werden, dass ein Befehl in der Regel mit einem Symbol und die Text angezeigt wird.  
  
 Symbole können sind 16 Pixel Breite x 16 Pixel hoch und entweder 8-Bit Farbtiefe (256 Farben) oder 32-Bit Farbtiefe ("true" Farbe). 32-Bit-Farbsymbole werden bevorzugt. Symbole werden in einer einzelnen horizontalen Zeile in einer einzelnen Bitmap, in der Regel angeordnet werden, obwohl mehrere Bitmaps zulässig sind. Diese Bitmap wird in der VSCT-Datei zusammen mit die einzelnen Symbole verfügbar sind, in der Bitmap deklariert. Finden Sie in der Referenz für die [Bitmaps-Element](../extensibility/bitmaps-element.md) Weitere Details.  
  
## <a name="adding-an-icon-to-a-command"></a>Hinzufügen eines Symbols zu einem Befehl  
 Das folgende Verfahren wird davon ausgegangen, dass Sie ein vorhandenes VSPackage-Projekt mit einem Menübefehl verfügen. Um herauszufinden, wie Sie dies tun, finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Erstellen einer Bitmap mit einer Farbtiefe von 32-Bit. Ein Symbol ist immer 16 x 16, sodass diese Bitmap 16 Pixel hoch sein muss und ein Vielfaches von 16 Pixel breit.  
  
     Jedes Symbol wird auf die Bitmap nebeneinander in einer einzelnen Zeile platziert. Verwenden Sie den alpha-Kanal, um Positionen in der Transparenz in jedes Symbol anzugeben.  
  
     Wenn Sie eine 8-Bit Farbtiefe verwenden, verwenden Sie Magenta, `RGB(255,0,255)`, wie die Transparenz. Allerdings werden die 32-Bit-Farbsymbole bevorzugt.  
  
2.  Kopieren Sie die Symboldatei, in das Verzeichnis "Resources" in Ihrem VSPackage-Projekt. Fügen Sie im Projektmappen-Explorer das Symbol zum Projekt hinzu. (Wählen Sie Ressourcen aus, und klicken Sie im Kontextmenü auf Hinzufügen, und klicken Sie dann auf Vorhandenes Element, und wählen Sie die Symboldatei.)  
  
3.  Öffnen Sie die VSCT-Datei im Editor.  
  
4.  Hinzufügen einer `GuidSymbol` Element mit dem Namen **TestIcon**. Erstellen Sie eine GUID (**Extras / erstellen GUID**, und wählen Sie dann **Registrierungsformat** , und klicken Sie auf Kopieren), und fügen Sie ihn in das `value` Attribut. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Hinzufügen einer `<IDSymbol>` für das Symbol. Die `name` -Attribut ist das Symbol "-ID, und die `value` seine Position für den Strip, der angibt, ob alle. Wenn nur ein Symbol vorhanden ist, fügen Sie 1 hinzu. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Erstellen Sie eine `<Bitmap>` in die `<Bitmaps>` Abschnitt der VSCT-Datei zum Darstellen der Bitmap, die die Symbole enthält.  
  
    -   Legen Sie die `guid` Wert, der den Namen des der `<GuidSymbol>` Element, die Sie im vorherigen Schritt erstellt haben.  
  
    -   Legen Sie die `href` Wert, der den relativen Pfad der Bitmapdatei (in diesem Fall **Ressourcen\\< Name der dokumentsymboldatei\>**.  
  
    -   Legen Sie die `usedList` Wert, der die IDSymbol, die Sie zuvor erstellt haben. Dieses Attribut gibt eine durch Trennzeichen getrennte Liste der Symbole in VSPackages verwendet werden. Symbole nicht in der Liste sind ausgeschlossene Formularkompilierung.  
  
         Die Bitmap-Block sollte wie folgt aussehen:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  In der vorhandenen `<Button>` -Element legen Sie die `Icon` Element auf die GUIDSymbol und IDSymbol-Werte, die Sie zuvor erstellt haben. Hier ist ein Beispiel für ein Button-Element mit diesen Werten:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Testen Sie Ihr Symbol. Erstellen Sie das Projekt, und starten Sie das Debugging. Suchen Sie der Befehl "" in der experimentellen Instanz. Es sollte dem Symbol angezeigt werden, dass Sie hinzugefügt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [VSCT-XML-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)
