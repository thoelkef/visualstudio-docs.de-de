---
title: "Organisieren von Objekten in Layoutcontainern im XAML-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Organisieren von Objekten in Layoutcontainern im XAML-Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stellen Sie sich vor, wo Objekte auf einer Seite angezeigt werden sollen; Objekte wie Bilder, Schaltflächen und Videos.  Möglicherweise sollen sie in Zeilen und Spalten in einer einzigen Zeile, vertikal oder horizontal oder an festen Positionen anzeigt werden.  
  
 Nachdem Sie die Möglichkeit gehabt haben, darüber nachzudenken, wie die Seite angezeigt werden kann, wählen Sie ein LayoutPanel\-Element.  Alle Seiten starten mit einem, da Ihre Objekte zu etwas hinzugefügt werden müssen.  Standardmäßig handelt es sich um ein **Raster** , aber Sie können es ändern.  
  
 LayoutPanel\-Elemente helfen Ihnen, Objekte auf einer Seite anzuordnen, aber sie können noch mehr.  Sie helfen Ihnen, für verschiedene Bildschirmgrößen und Auflösungen zu entwerfen.  Wenn Benutzer Ihre Anwendung ausführen, wird alles in einem Layoutpanel passend zur Bildschirmfläche des Geräts angepasst.  Wenn Sie dies nicht möchten, können Sie dieses Verhalten für einen Teil des Layouts oder das gesamte Layout natürlich überschreiben.  Um dies zu steuern, können Sie Höhen\-und Breiteneigenschaften verwenden.  
  
 Diese Seite beschreibt LayoutPanel\-Elemente und Steuerelemente und leitet Sie dann weiter zu kurzen Videos, mit deren Hilfe sie einen Einstieg finden.  
  
> [!NOTE]
>  Einige Videos beziehen sich möglicherweise auf Blend oder Expression Blend, die den gleichen XAML\-Designer wie Visual Studio und Blend für Visual Studio verwenden.  
  
## Layoutbereiche  
 Starten Sie die Seite durch Auswahl eines dieser Layoutpanels.  Ihre Seite kann mehrere Panele enthalten.  Sie können z. B. beginnen mit einem **Rasterpanel** und dann einen **StackPanel** in einen Bereich im **Raster** hinzufügen, sodass Sie Steuerelemente in diesem Element vertikal anordnen können.  
  
 Die folgenden LayoutPanel\-Elemente sind die meisten allgemein verwendeten, aber es gibt noch andere.  Sie befinden sich im Bereich **Bestand**.  
  
-   [Raster](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Raster  
 Anordnen von Objekten in Zeilen und Spalten.  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Using Grids](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids) \(Verwenden von Rastern\) \(in englischer Sprache\)  
  
###  <a name="Uniform"></a> UniformGrid  
 Anordnen von Objekten in gleiche oder einheitliche Rasterbereiche.  Dieser Bereich eignet sich hervorragend für die Anordnung einer Liste von Bildern.  
  
 \(Nur für WPF\-Projekte verfügbar\)  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with a UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid) \(Arbeiten mit einem UniformGrid\) \(in englischer Sprache\)  
  
###  <a name="Canvas"></a> Canvas  
 Anordnen von Objekten auf jede gewünschte Weise.  Wenn Benutzer Ihre Anwendung ausführen, haben diese Elemente feste Positionen auf dem Bildschirm.  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with the canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas) \(Arbeiten mit der Canvas\) \(in englischer Sprache\)  
  
###  <a name="Stack"></a> StackPanel  
 Horizontales oder vertikales Anordnen von Objekten in einer einzelnen Zeile.  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) \(Arbeiten mit StackPanel und WrapPanel\) \(in englischer Sprache\)  
  
###  <a name="Wrap"></a> WrapPanel  
 Anordnen von Objekten nacheinander von links nach rechts.  Wenn der Bereich am rechten Rand nicht genügend Platz aufweist, wird der Inhalt in die nächste Zeile von links nach rechts, oben nach unten *umschlossen*.  Sie können auch die ein WrapPanel\-Element vertikal ausrichten, sodass Objekte von oben nach unten und von links nach rechts fließen.  
  
 \(Nur für WPF\-Projekte verfügbar\)  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) \(Arbeiten mit StackPanel und WrapPanel\) \(in englischer Sprache\)  
  
###  <a name="Dock"></a> DockPanel  
 Ordnet Elemente an, sodass sie an einer Kante des Panels bleiben oder *andocken*.  
  
 \(Nur für WPF\-Projekte verfügbar\)  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo) \(in englischer Sprache\)  
  
## Layout\-Steuerelemente  
 Sie können Ihre Objekte auch zu Layout\-Steuerelementen hinzufügen.  Sie sind haben keinen Funktionsumfang wie ein Layoutpanel, aber Sie werden für bestimmte Szenarien nützlich sein.  
  
 Die folgenden LayoutPanel\-Elemente sind die meisten, allgemein verwendeten, aber es gibt noch andere.  Sie befinden sich im Bereich **Bestand**.  
  
-   [Randbereich](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Randbereich  
 Erstellen Sie einen Rahmen, Hintergrund oder beides rund um ein Objekt.  Sie können nur ein Objekt zu einem **Rahmen** hinzufügen.  Wenn Sie einen Rahmen oder Hintergrund für mehr als ein Objekt anwenden möchten, fügen Sie ein LayoutPanel\-Element zum **Rahmen** hinzu.  Dann fügen Sie Objekte zu diesem Panel oder Steuerelement hinzu.  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Working with Borders](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders) \(Arbeiten mit Rahmen\) \(in englischer Sprache\)  
  
###  <a name="Popup"></a> Popup  
 Anzeigen von Informationen oder Optionen für Benutzer in einem Fenster.  Sie können nur ein Objekt zu einem **Rahmen** hinzufügen.  In der Standardeinstellung enthält ein **Popup** ein **Raster**, kann jedoch geändert werden.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Ermöglicht Benutzern, den Bildlauf auf einer Seite oder ein einem Bereich zu verwenden.  Sie können nur ein Objekt zu einem **ScrollViewer** hinzufügen, deshalb ist es sehr sinnvoll, ein LayoutPanel\-Element, wie z. B. ein **Raster**\- oder **StackPanel**, hinzuzufügen.  
  
###  <a name="View"></a> Viewbox  
 Skalieren von Objekten ähnlich wie bei einem Zoomsteuerelement.  Sie können nur ein Objekt zu einer **Viewbox** hinzufügen.  Wenn Sie diesen Effekt auf mehr als ein Objekt anwenden möchten, fügen Sie ein Layoutpanel zur **ViewBox** und danach Ihre Steuerelemente zu diesem LayoutPanel hinzu.  
  
 \(Nur für WPF\-Projekte verfügbar\)  
  
## Siehe auch  
 [Arbeiten mit Elementen im XAML\-Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Erstellen einer Benutzeroberfläche mit dem XAML\-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)