---
title: "Festlegen von Farben, Farbverl&#228;ufen und Deckkraft | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestaltung von UI-Elementen [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Festlegen von Farben, Farbverl&#228;ufen und Deckkraft
Alle Benutzeroberflächenelemente \(UI\-Elemente\) in Visual Studio werden in Windows Presentation Foundation \(WPF\) erstellt. Daher können Sie, wenn Sie Toolfenster oder andere UI\-Elemente erstellen, Farben, Farbverläufe und Deckkraft dadurch anwenden, dass Sie die entsprechenden Attribute dieser Elemente festlegen. Sie können diese Attribute auf bestimmte Werte festlegen, indem Sie das **Eigenschaften**\-Fenster verwenden, oder Sie können die integrierte Entwicklungsumgebung \(IDE\) hinsichtlich der Systemwerte abfragen. Sie sollten Systemwerte verwenden, wenn Sie möchten, dass Ihre Erweiterungen so aussehen wie die anderen Teile der IDE.  
  
 Windows Forms\-UI und UI in systemeigenem Code werden aus Gründen der Abwärtskompatibilität weiterhin unterstützt. Informationen, wie Farben und Farbverläufe in Nicht\-WPF\-Erweiterungen festgelegt werden, finden Sie in der Dokumentation von [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
## Festlegen von Farben, Farbverläufen und Deckkraft  
 Sie können die Darstellung der meisten XAML\-Elemente festlegen, indem Sie deren `Background`, `Foreground`, `Opacity` oder anderen visuellen Attribute festlegen. Diese Attribute entsprechen Eigenschaften, die ein <xref:System.Windows.Media.Brush?displayProperty=fullName>\-Objekt als Wert annehmen.  
  
#### So legen Sie Hintergrundfarben, Farbverläufe und Deckkraft in einem Toolfenster fest  
  
1.  Öffnen Sie „MeinSteuerelement.xaml“.  
  
2.  Geben Sie im **XAML**\-Bereich im <xref:System.Windows.Controls.UserControl>\-Element der obersten Ebene die Zeichenfolge `background=` ein.  
  
     IntelliSense zeigt eine Liste von Farben für das BackGround\-Attribut an.  
  
     Wählen Sie eine Farbe in der Liste aus.  
  
3.  Erweitern Sie im **Eigenschaften**\-Fenster den **Pinsel**\-Knoten, und klicken Sie dann auf **Hintergrund**.  
  
     Im **Eigenschaften**\-Fenster wird ein Farbwähler angezeigt. Über dem Farbwähler befindet sich eine Reihe von Symbolen, die Pinsel darstellen.  
  
4.  Verwenden Sie die Schieberegler, um eine Farbe auszuwählen.  
  
     Der XAML\-Code wird sofort aktualisiert, um die neue Hintergrundfarbe zu zeigen.  
  
5.  Klicken Sie auf das Farbverlaufspinsel\-Symbol.  
  
     Der Farbwähler wird in einen Farbverlaufswähler geändert.  
  
6.  Verwenden Sie die Schieberegler, um einen Farbverlauf auszuwählen.  
  
     Der XAML\-Code wird sofort aktualisiert, um die neue Hintergrundfarbe zu zeigen.  
  
7.  Klicken Sie auf das Bildpinsel\-Symbol.  
  
     Der Farbverlaufswähler wird in ein Bildauswahltool geändert.  
  
8.  Wählen Sie ein Bild aus, und legen Sie dessen Parameter für Strecken und Kachel fest.  
  
     Der XAML\-Code wird sofort aktualisiert, um das neue Hintergrundbild zu zeigen.  
  
9. Klicken Sie auf das Nullpinsel\-Symbol.  
  
     Der Hintergrund im Designer wird auf neutral zurückgesetzt, und das `BackGround`\-Attribut wird auf `"{x:Null}"` festgelegt.  
  
## Abfragen von Systemwerten  
 Sie können Systemwerte abfragen, indem Sie die <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName>\-Klasseneigenschaften verwenden, die auf Pinsel verweisen, die in anderen Teilen von Visual Studio festgelegt sind.  
  
#### So legen Sie Farben, Farbverläufe und Deckkraft durch Abfragen von Systemwerten fest  
  
1.  Wählen Sie ein XAML\-Element aus.  
  
2.  Legen Sie in der Elementdefinition eins der visuellen Attribute des Elements auf eine Eigenschaft der `VsBrushes`\-Klasse fest \(siehe folgendes Beispiel\).  
  
     [!code-xml[TWShortcutMenu#32](../misc/codesnippet/Xaml/setting-colors-gradients-and-opacity_1.xaml)]  
  
     Durch Verwenden der [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md)\-Erweiterung kann der Wert nach Bedarf geändert werden, etwa wenn ein Benutzer die Einstellungen ändert. Sie müssen die [x:Static](../Topic/x:Static%20Markup%20Extension.md)\-Erweiterung verwenden, weil die `VsBrushes`\-Klasse nicht zum Standard\-WPF\-Namespace gehört.  
  
## Siehe auch  
 [Erweitern von Toolfenstern](../misc/extending-tool-windows.md)