---
title: "Architektur der Startseite | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Architektur der Startseite"
  - "XAML-Code für die Startseite"
ms.assetid: f94afe27-0be3-47d9-8e17-b0fd429017bd
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Architektur der Startseite
Dieses Dokument beschreibt die Architektur des Fensters Tool Seiten starten in Visual Studio enthalten ist.  Sie können diese Informationen verwenden, um Elemente auf der Startseite hinzuzufügen oder zu ändern, ohne die zugrunde liegende Struktur zu ändern.  
  
 Die Visual Studio\-Startseite ist in Extensible Application Markup Language. B. Windows Presentation Foundation \(WPF\) \(XAML\) geschrieben.  Weitere Informationen über das XAML\-Markup finden Sie unter [Übersicht über XAML \(WPF\)](../Topic/XAML%20Overview%20\(WPF\).md).  
  
## Seiten\-Struktur  
 Die Startseite besteht aus einem <xref:System.Windows.Controls.Image>\-Element und <xref:System.Windows.Controls.Grid> aus zwei Elementen in einem `Grid`Element der obersten Ebene.  Das `Image`\-Element umfasst die oberste Position des Toolfensters und enthält das Visual Studio\-Logo.  Unterhalb des Logos enthält das linke `Grid`Element die Befehlsschaltflächen für neue Projekte, die **Zuletzt geöffnete Projekte** Liste und einen Bereich für Startseiten Optionen festgelegt.  Das Recht `Grid`Element enthält ein <xref:System.Windows.Controls.TabControl>\-Element, das eine **Erste Schritte** eine Registerkarte **Leitfaden und Ressourcen** Registerkarte und eine **Aktuelle Nachrichten** Registerkarte verfügt.  Eine zentrale Spalte wird zwischen dem linken und dem rechten `Grid`Elementen definiert, aber keinen Inhalt hat, und ist nur als Abstandhalter verwendet.  
  
### Fenster\-Text  
 Der Hintergrund des Toolfensters erfolgt über das `Grid`Element der obersten Ebene dargestellt.  Die Breiten der Spalten im Folgenden werden `ColumnDefinitions`\-Element definiert.  Die Höhe des Logos Bilder werden im `RowDefinitions`\-Element festgelegt.  
  
 Spaltendefinitionen und Zeilendefinitionen werden in den nullbasierten Arrays gespeichert.  Um ein Element in einem Raster zu positionieren, legen Sie die `Grid.Column` und `Grid.Row` die Attribute fest <xref:System.Windows.Controls.ColumnDefinition> entsprechenden Indizes und der <xref:System.Windows.Controls.RowDefinition>\-Elemente entspricht.  
  
### Logo\-Image  
 Das Visual Studio\-Logo nimmt die oberste Zeile des Rasters der obersten Ebene \(`Grid.Row="0"`\) als `Image`\-Element.  Um ein anderes Bild anzuzeigen, zeigen Sie das `Source``Image`\-Attribut des Elements auf einer anderen Bilddatei.  Um das Bild zu entfernen, deaktivieren Sie das `Image`\-Element, und legen Sie das `height`\-Attribut des entsprechenden `RowDefinition`\-Elements der obersten Ebene `0` \(null\) fest, dass die oberste Zeile des Datenblatts auszublenden.  
  
### Linke Spalte  
 Die linke Spalte wird von der Startseite `Grid`ein Element gerade `Grid.Column="0"` und `Grid.Row="1"`dargestellt.  Dieses Element enthält Definitionen für drei Zeilen, die das Befehlsschaltflächen Eigenschaftenraster, um das neue Projekt `StackPanel`\-Element und ein Raster von Visual Studio\-Optionen anzuzeigen.  
  
 Sie können ein Element diesem Raster hinzufügen, indem Sie es an eine der vorhandenen Zeilen hinzufügen oder indem Sie eine neue Zeilen hinzufügen. Die Definition  Wenn Sie eine neue Zeile definieren, denken Sie daran, die `Grid.Row`\-Werte aller Elemente zu erhöhen, die mit der neuen Zeile stehen.  
  
### Mittlere Spalte  
 Die mittlere Spalte ist ein Abstandhalter und enthält keine Elemente.  Um ein Element der mittleren Spalte hinzuzufügen, positionieren Sie sie unter `Grid.Column="1"` und `Grid.Row="1"`.  Stellen Sie sicher, das `Width`\-Attribut der Spaltendefinition anpassen, um die Änderung zu berücksichtigen.  
  
### Rechte Spalte  
 Die rechte Spalte enthält ein `Grid`\-Element am `Grid.Column="1"` und `Grid.Row="1"`.  Das Raster enthält ein `TabControl`\-Element, das über drei Registerkarten verfügt.  
  
 Sie können eine Registerkarte hinzu, indem Sie ein <xref:System.Windows.Controls.TabItem>\-Element, das Registersteuerelement angezeigt, wie in [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)hinzufügen oder vorhandene Tabstopps bearbeiten oder entfernen.  Registerkarten finden in der Benutzeroberfläche in derselben Reihenfolge von links nach rechts ausgewertet, in der sie im Markup von oben nach unten angezeigt werden.  
  
 Wenn Sie ein Element am Raster der rechten Spalte außerhalb des Registersteuerelements hinzufügen, wird empfohlen, eine neue Zeile oder Spalte im Raster definieren, um sicherzustellen, dass sie erwartungsgemäß angezeigt wird.  
  
## Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Startseite – Bewährte Methoden](../misc/start-page-best-practices.md)   
 [Bereitstellen von benutzerdefinierte Startseiten](../extensibility/deploying-custom-start-pages.md)