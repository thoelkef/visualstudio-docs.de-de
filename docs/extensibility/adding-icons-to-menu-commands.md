---
title: "Hinzuf&#252;gen von Symbolen zu Men&#252;befehlen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbole [Visual Studio], hinzufügen zu Symbolleisten"
  - "Symbolleisten [Visual Studio], Hinzufügen von Symbolen zu Befehlen"
  - "Befehle [Visual Studio], Hinzufügen von Symbolen"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Hinzuf&#252;gen von Symbolen zu Men&#252;befehlen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Befehle können in Menüs und Symbolleisten angezeigt werden. Auf Symbolleisten ist es üblich, für einen Befehl mit nur einem Symbol \(um Speicherplatz zu sparen\) und in Menüs angezeigt werden, dass ein Befehl in der Regel mit einem Symbol und der Text angezeigt wird.  
  
 Symbole sind 16 Pixel breit und 16 Pixel hoch und 8\-Bit\-Farbtiefe \(256 Farben\) oder 32\-Bit\-Farbtiefe \(true Color\) sein können. 32\-Bit\-Farbsymbole werden bevorzugt. Symbole sind normalerweise in einer einzelnen horizontalen Zeile in einer einzelnen Bitmap, angeordnet, obwohl mehrere Bitmaps zulässig sind. Diese Bitmap ist in der VSCT\-Datei sowie die einzelnen Symbole in der Bitmap verfügbar deklariert. Finden Sie in der Referenz für die [Bitmaps\-Element](../extensibility/bitmaps-element.md) für weitere Details.  
  
## Hinzufügen eines Symbols zu einem Befehl  
 Das folgende Verfahren wird davon ausgegangen, dass Sie ein vorhandenes VSPackage\-Projekt mit einem Menübefehl verfügen. Informationen hierzu finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Erstellen einer Bitmap mit einer Farbtiefe von 32 Bits. Ein Symbol ist immer 16 x 16, sodass diese Bitmap 16 Pixel hoch sein muss und ein Vielfaches von 16 Pixel breit.  
  
     Jedes Symbol wird in der Bitmap nebeneinander in einer einzelnen Zeile platziert. Verwenden Sie den alpha\-Kanal, um Positionen in der Transparenz in jedes Symbol anzugeben.  
  
     Wenn Sie eine Farbtiefe von 8\-Bit verwenden, verwenden Sie Magenta, `RGB(255,0,255)`, wie die Transparenz. Allerdings werden die 32\-Bit\-Farbsymbole bevorzugt.  
  
2.  Kopieren Sie die Symboldatei für das Ressourcenverzeichnis in VSPackage\-Projekt. Fügen Sie im Projektmappen\-Explorer das Symbol zum Projekt hinzu. \(Wählen Sie Ressourcen aus, und klicken Sie im Kontextmenü auf Hinzufügen, und klicken Sie dann auf Vorhandenes Element, und wählen Sie die Symboldatei.\)  
  
3.  Öffnen Sie die VSCT\-Datei im Editor.  
  
4.  Hinzufügen einer `GuidSymbol` Element mit dem Namen **TestIcon**. Erstellen Sie eine GUID \(**Extras \/ erstellen GUID**, und wählen Sie dann **Registrierungsformat** und klicken Sie auf Kopieren\), und fügen Sie ihn in die `value` Attribut. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Hinzufügen einer `<IDSymbol>` für das Symbol. Das `name` \-Attribut ist das Symbol\-ID und die `value` Gibt die Position auf der Leiste an, ob alle. Wenn nur ein Symbol vorhanden ist, fügen Sie 1 hinzu. Das Ergebnis sollte wie folgt aussehen:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Erstellen einer `<Bitmap>` in der `<Bitmaps>` \-Abschnitt der VSCT\-Datei zur Darstellung der Bitmap, die die Symbole enthält.  
  
    -   Festlegen der `guid` Wert, der den Namen der `<GuidSymbol>` Element, die Sie im vorherigen Schritt erstellt haben.  
  
    -   Festlegen der `href` Wert, der den relativen Pfad der Bitmap\-Datei \(in diesem Fall **Ressourcen\\ \< Symboldateinamen \>**.  
  
    -   Festlegen der `usedList` Wert, der die IDSymbol, die Sie zuvor erstellt haben. Dieses Attribut gibt eine durch Kommas getrennte Liste der Symbole in das VSPackage verwendet werden. Die Symbole nicht in der Liste sind ausgeschlossene Formularkompilierung.  
  
         Die Bitmap\-Block sollte wie folgt aussehen:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  In der vorhandenen `<Button>` \-Element die `Icon` Element an die GUIDSymbol und IDSymbol\-Werte, die Sie zuvor erstellt haben. Hier ist ein Beispiel für ein Button\-Element mit diesen Werten:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Testen Sie das Symbol. Erstellen Sie das Projekt, und starten Sie das Debugging. Suchen Sie in der experimentellen Instanz den Befehl. Es sollte dem Symbol angezeigt werden, dass Sie hinzugefügt.  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML\-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)