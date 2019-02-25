---
title: Aktualisieren von Anpassungen von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f57356cfe2d382ec0f4199555515e08e765e9486
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634928"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualisieren von Anpassungen von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden
  Wenn Ihr Projekt eine menübandanpassung, die erstellt wurde die **Menüband (visueller Designer)** Projektelement, müssen Sie die folgenden Änderungen an Ihrem Projektcode vornehmen, wenn das Zielframework geändert wird, um die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder später noch mal.

-   Ändern Sie den generierten Menübandcode.

-   Ändern Sie Code, in dem Menüband-Steuerelemente zur Laufzeit instanziiert werden, Menübandereignisse behandelt werden oder die Position einer Menübandkomponente programmgesteuert festgelegt wird.

## <a name="update-the-generated-ribbon-code"></a>Aktualisieren Sie den generierten Menübandcode
 Wenn das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie den generierten Code für das Menübandelement ändern, indem Sie die folgenden Schritte ausführen. Die zu aktualisierenden Codedateien hängen von der Programmiersprache ab und davon, wie Sie das Projekt erstellt haben:

-   In Visual Basic-Projekten oder in Visual C#-Projekten, die Sie in einem erstellt [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] oder [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] führen Sie alle Schritte in der Menüband-Code-Behind-Datei (*YourRibbonItem*. "Designer.cs" oder *YourRibbonItem*. Designer.vb). Um den Code-Behind-Datei in Visual Basic-Projekten anzuzeigen, klicken Sie auf die **alle Dateien anzeigen** Schaltfläche **Projektmappen-Explorer**.

-   In Visual C#-Projekten, die Sie in Visual Studio 2008 erstellt und anschließend eine Aktualisierung auf [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], führen Sie die ersten beiden Schritte aus, in der Menüband-Codedatei (*YourRibbonItem*.cs oder *YourRibbonItem*. vb), und Führen Sie die verbleibenden Schritte aus, in der Menüband-Code-Behind-Datei.

### <a name="to-change-the-generated-ribbon-code"></a>So ändern Sie den generierten Menübandcode

1.  Ändern Sie die Deklaration der Ribbon-Klasse so, dass sie von <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> statt von `Microsoft.Office.Tools.Ribbon.OfficeRibbon` abgeleitet wird.

2.  Ändern Sie den Konstruktor der Ribbon-Klasse, wie unten dargestellt. Ändern Sie den Code nicht, wenn Sie dem Konstruktor eigenen Code hinzugefügt haben. Ändern Sie in Visual Basic-Projekten nur den parameterlosen Konstruktor. Ignorieren Sie den anderen Konstruktor.

     Im folgenden Codebeispiel wird der Standardkonstruktor einer Ribbon-Klasse in einem Projekt dargestellt, das auf .NET Framework 3.5 abzielt.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     Im folgenden Codebeispiel wird der Standardkonstruktor einer Menübandklasse in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet ist.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3.  Ändern Sie in der `InitializeComponent`-Methode Code, in dem ein Menübandsteuerelement erstellt wird, damit im Code stattdessen eine der Hilfsmethoden des <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>-Objekts verwendet wird.

    > [!NOTE]
    >  In Visual C#-Projekten müssen Sie den Bereich mit der Bezeichnung `Component Designer generated code` erweitern, um die `InitializeComponent`-Methode anzuzeigen.

     Angenommen, die Datei enthält die folgende Codezeile, die eine <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> mit der Bezeichnung `button1` in einem Projekt instanziiert, das auf .NET Framework 3.5 abzielt.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     In einem Projekt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet ist, müssen Sie stattdessen den folgenden Code verwenden.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Eine vollständige Liste der Hilfsmethoden für die Multifunktionsleisten-Steuerelemente, finden Sie unter [Menüband instanziieren steuert](#ribboncontrols).

4.  Ändern Sie in Visual C#-Projekten jede Codezeile in der `InitializeComponent`-Methode, die einen <xref:System.EventHandler%601>-Delegaten verwendet, um stattdessen einen bestimmten Menübanddelegaten zu verwenden.

     Angenommen, die Datei enthält die folgende Codezeile, die das <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>-Ereignis in einem Projekt behandelt, das auf .NET Framework 3.5 abzielt.

    <CodeContentPlaceHolder>8</CodeContentPlaceHolder> in einem Projekt, das [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, Sie müssen stattdessen den folgenden Code.

    <CodeContentPlaceHolder>9</CodeContentPlaceHolder> eine vollständige Liste der Menübanddelegaten finden Sie unter [Behandeln von Menübandereignissen](#ribbonevents).

5.  Suchen Sie in Visual Basic-Projekten die `ThisRibbonCollection`-Klasse am Ende der Datei. Ändern Sie die Deklaration dieser Klasse, sodass sie nicht mehr von `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection` erbt.

##  <a name="ribboncontrols"></a> Instanziieren von Menübandsteuerelementen
 Sie müssen jeden Code ändern, in dem Menübandsteuerelemente dynamisch instanziiert werden. In Projekten, die auf .NET Framework 3.5 abzielen, sind Menübandsteuerelemente Klassen, die Sie in bestimmten Szenarien direkt instanziieren können. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, fungieren diese Steuerelemente als Schnittstellen, die Sie nicht direkt instanziieren können. Sie müssen die Steuerelemente mit Methoden erstellen, die vom <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>-Objekt bereitgestellt werden.

 Es gibt zwei Möglichkeiten, um auf das <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>-Objekt zuzugreifen:

- Mithilfe der Factory-Eigenschaft der Ribbon-Klasse zu verwenden. Verwenden Sie diesen Ansatz aus Code in der Ribbon-Klasse.

- Mithilfe der `Globals.Factory.GetRibbonFactory`-Methode. Verwenden Sie diesen Ansatz aus Code außerhalb der Ribbon-Klasse. Weitere Informationen zu der Globals-Klasse, finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

  Im folgenden Codebeispiel wird dargestellt, wie ein <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> in einer Menübandklasse eines Projekts erstellt wird, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet ist.

<CodeContentPlaceHolder>10</CodeContentPlaceHolder>
<CodeContentPlaceHolder>11</CodeContentPlaceHolder> die folgende Tabelle enthält die Steuerelemente, die Sie programmgesteuert erstellen können und die Methode zum Erstellen der Steuerelemente in Projekten, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher.

|Steuerelement|RibbonFactory-Methode für Projekte unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

##  <a name="ribbonevents"></a> Behandeln von Menübandereignissen
 Sie müssen Code ändern, in dem Ereignisse von Menübandsteuerelementen behandelt werden. In Projekten, die auf .NET Framework 3.5 abzielen, werden diese Ereignisse vom generischen <xref:System.EventHandler%601>-Delegaten behandelt. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, werden diese Ereignisse jetzt von anderen Delegaten behandelt.

 In der folgenden Tabelle sind die Menübandereignisse und die Delegaten aufgeführt, die ihnen in Projekten zugeordnet sind, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind.

|event|Delegat für Projekte unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>-Ereignis in einer generierten Ribbon-Klasse|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Die Position einer Menübandkomponente programmgesteuert festgelegt
 Sie müssen Code ändern, in dem die Position von Menübandgruppen, Registerkarten oder Steuerelementen festgelegt wird. In Projekten, die auf .NET Framework 3.5 abzielen, können Sie mithilfe der `AfterOfficeId`-Methode und der `BeforeOfficeId`-Methode der statischen `Microsoft.Office.Tools.Ribbon.RibbonPosition`-Klasse die `Position`-Eigenschaft von Gruppen, Registerkarten oder Steuerelementen zuweisen. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, müssen Sie auf diese Methoden mit der <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A>-Eigenschaft zugreifen, die vom <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>-Objekt bereitgestellt wird.

 Es gibt zwei Möglichkeiten, um auf das <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>-Objekt zuzugreifen:

- Mithilfe der `Factory`-Eigenschaft der Ribbon-Klasse. Verwenden Sie diesen Ansatz aus Code in der Ribbon-Klasse.

- Mithilfe der `Globals.Factory.GetRibbonFactory`-Methode. Verwenden Sie diesen Ansatz aus Code außerhalb der Ribbon-Klasse. Weitere Informationen zu der Globals-Klasse, finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

  Im folgenden Codebeispiel wird dargestellt, wie die `Position`-Eigenschaft einer Registerkarte in einer Ribbon-Klasse in einem Projekt festgelegt wird, das auf .NET Framework 3.5 abzielt.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Im folgenden Codebeispiel wird die gleiche Aufgabe in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] abzielt.

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Siehe auch
- [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
