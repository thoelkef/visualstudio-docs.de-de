---
title: Hinzufügen von Symbolen zu Menübefehlen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740153"
---
# <a name="add-icons-to-menu-commands"></a>Hinzufügen von Symbolen zu Menübefehlen
Befehle können sowohl in Menüs als auch auf Symbolleisten angezeigt werden. Auf Symbolleisten ist es üblich, dass ein Befehl nur mit einem Symbol angezeigt wird (um Platz zu sparen), während in Menüs ein Befehl in der Regel sowohl mit einem Symbol als auch mit Text angezeigt wird.

 Symbole sind 16 Pixel breit und 16 Pixel hoch und können entweder 8-Bit-Farbtiefe (256 Farben) oder 32-Bit-Farbtiefe (wahre Farbe) sein. 32-Bit-Farbsymbole werden bevorzugt. Symbole sind in der Regel in einer einzelnen horizontalen Zeile in einer einzelnen Bitmap angeordnet, obwohl mehrere Bitmaps zulässig sind. Diese Bitmap wird in der *.vsct-Datei* zusammen mit den einzelnen Symbolen deklariert, die in der Bitmap verfügbar sind. Weitere Informationen finden Sie in der Referenz für das [Bitmaps-Element.](../extensibility/bitmaps-element.md)

## <a name="add-an-icon-to-a-command"></a>Hinzufügen eines Symbols zu einem Befehl
 Im folgenden Verfahren wird davon ausgegangen, dass Sie über ein vorhandenes VSPackage-Projekt mit einem Menübefehl verfügen. Informationen dazu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Erstellen Sie eine Bitmap mit einer Farbtiefe von 32 Bit. Ein Symbol ist immer 16 x 16, so dass diese Bitmap 16 Pixel hoch und ein Vielfaches von 16 Pixel breit sein muss.

     Jedes Symbol wird in einer einzigen Zeile nebeneinander auf der Bitmap platziert. Verwenden Sie den Alphakanal, um in jedem Symbol Transparenzstellen anzugeben.

     Wenn Sie eine 8-Bit-Farbtiefe verwenden, verwenden Sie Magenta, `RGB(255,0,255)`, als Transparenz. 32-Bit-Farbsymbole werden jedoch bevorzugt.

2. Kopieren Sie die Symboldatei in das *Ressourcenverzeichnis* in Ihrem VSPackage-Projekt. Fügen Sie im **Projektmappen-Explorer**das Symbol zum Projekt hinzu. (Wählen Sie **Ressourcen**aus, und klicken Sie im Kontextmenü auf **Hinzufügen**, dann **Auf "Vorhandenes Element**", und wählen Sie die Symboldatei aus.)

3. Öffnen Sie die *.vsct-Datei* im Editor.

4. Fügen `GuidSymbol` Sie ein Element mit dem Namen **testIcon**hinzu. Erstellen Sie eine GUID (**Tools** > **GuiD erstellen**, wählen Sie dann **Registrierungsformat** aus und klicken Sie auf **Kopieren**), und fügen Sie sie in das `value` Attribut ein. Das Ergebnis sollte wie folgt aussehen:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Fügen `<IDSymbol>` Sie ein für das Symbol hinzu. Das `name` Attribut ist die ID des `value` Symbols, und der gibt seine Position auf dem Streifen an, falls vorhanden. Wenn nur ein Symbol vorhanden ist, fügen Sie 1 hinzu. Das Ergebnis sollte wie folgt aussehen:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Erstellen `<Bitmap>` Sie `<Bitmaps>` eine im Abschnitt der *.vsct-Datei,* um die Bitmap darzustellen, die die Symbole enthält.

    - Legen `guid` Sie den Wert `<GuidSymbol>` auf den Namen des Elements fest, das Sie im vorherigen Schritt erstellt haben.

    - Legen `href` Sie den Wert auf den relativen Pfad der Bitmapdatei fest (in diesem Fall **<\\ Symboldateinamen\>**.

    - Legen `usedList` Sie den Wert auf das ZUVOR erstellte IDSymbol fest. Dieses Attribut gibt eine durch Kommas getrennte Liste der Symbole an, die im VSPackage verwendet werden sollen. Symbole, die nicht in der Liste aufgeführt sind, werden für die Formularkompilierung ausgeschlossen.

         Der Bitmap-Block sollte wie folgt aussehen:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Legen Sie `<Button>` im vorhandenen `Icon` Element das Element auf die zuvor erstellten GUIDSymbol- und IDSymbol-Werte fest. Hier ist ein Beispiel für ein Button-Element mit diesen Werten:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testen Sie Ihr Symbol. Erstellen Sie das Projekt, und starten Sie das Debugging. Suchen Sie in der experimentellen Instanz den Befehl. Es sollte das Symbol zeigen, das Sie hinzugefügt haben.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [VSCT-XML-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)
