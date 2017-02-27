---
title: "Einf&#252;gen von Steuerelementen und &#196;ndern des Verhaltens im XAML-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Einf&#252;gen von Steuerelementen und &#196;ndern des Verhaltens im XAML-Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Steuerelemente ermöglichen Benutzern die Interaktion mit Ihrer Anwendung. Verwenden sie zum Sammeln von Informationen und zum Durchführen von Aktionen verwenden, wie z. B. Animieren eines Objekts oder eine Datenquelle.  
  
 **In diesem Thema:**  
  
-   [Hinzufügen von Steuerelementen zur Zeichenfläche](#Insert)  
  
-   [Mit Steuerelementen Dinge ausführen](#Modify)  
  
##  <a name="Insert"></a> Hinzufügen von Steuerelementen zur Zeichenfläche  
 Sie können Steuerelemente über den Bereich **Bestand** auf die **Zeichenfläche** ziehen und sie dann im Fenster **Eigenschaften** ändern.  
  
 ![Blend &#45; Posten &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend\_AssetsFlipView\_XAML")  
  
 In diesen Videos erfahren Sie, wie Sie einige der häufigeren Steuerelemente verwenden.  
  
|Steuerelement|Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):|  
|-------------------|---------------------------------------------------------------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c\-0b2b\-4253\-ac57\-b86fcb8c9591")|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Hinzufügen der Steuerelemente](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779\-a68f\-436b\-b834\-a91b7995a3ec")|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Entwerfen einer Schaltfläche](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963\-00f7\-4a33\-abcd\-b0849edebada")|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Hinzufügen von Bildern zu einem Textblock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92\-3c74\-4218\-815c\-e98c930ac189")|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Erstellen eines Schiebereglers und einer QuickInfo](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f\-a27e\-4a8f\-95aa\-8a4e8b4ee7be")|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Arbeiten mit einem GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### Erstellen eines Steuerelements aus dem Abbild, einer Form oder einem Pfad  
 Sie können ein Objekt in ein Steuerelement verwandeln.  
  
 ![Dialogfeld "Into&#45;Steuerelement erstellen" in Blend](../designers/media/blend_makeintocontrol_xaml.png "blend\_MakeIntoControl\_XAML")  
  
 Stellen Sie sich beispielsweise ein Bild von einem Fernseher in der Mitte der Seite vor. Sie können Steuerelemente aus kleinen Bildern konvertieren, die wie TV\-Schaltflächen aussehen. Benutzer können dann auf diese Schaltflächen klicken, um den Kanal zu ändern.  
  
 Dies ist möglich, da die Schaltflächen nun Steuerelemente sind. Mit den Steuerelementen können Sie auf Benutzerinteraktionen reagieren; in diesem Fall, wenn der Benutzer auf eine Schaltfläche klickt.  
  
 Wählen Sie ein Objekt, um ein Steuerelement zu erstellen. Klicken Sie im Menü **Extras** auf **Steuerung erstellen**.  
  
##  <a name="Modify"></a> Mit Steuerelementen Dinge ausführen  
 Steuerelemente können Aktionen ausführen, wenn die Benutzer mit ihnen interagieren. Sie können z. B. eine Animation starten, eine Datenquelle aktualisieren oder ein Video abspielen.  
  
 Verwenden Sie *Trigger*, *Verhalten* und *Ereignisse*, um mit Steuerelementen etwas auszuführen.  
  
### Trigger  
 Ein *Trigger* ändert eine Eigenschaft oder führt eine Aufgabe als Reaktion auf ein Ereignis oder eine Änderung an einer anderen Eigenschaft aus. Beispielsweise können Sie die Farbe einer Schaltfläche ändern, wenn Benutzer darauf zeigen.  
  
 ![Der Bereich "Trigger"](../designers/media/custom_button_blend_propertytriggerinfo.png "custom\_button\_blend\_PropertyTriggerInfo")  
  
 **Sehen Sie sich ein kurzes Video an \(nur in englischer Sprache verfügbar\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Hinzufügen eines Eigenschaftentriggers](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### Verhalten  
 Ein *Verhalten* ist ein wiederverwendbares Code\-Paket. Sie können damit mehr tun als nur Eigenschaften zu ändern. Sie können Aktionen wie das Abfragen eines Datendienstes ausführen. Blend enthält eine kleine Sammlung, Sie können jedoch weitere hinzufügen. Ziehen Sie ein Verhalten auf ein beliebiges Objekt auf der Zeichenfläche und passen Sie das Verhalten durch Festlegen von Eigenschaften an.  
  
 ![FluidMoveBehavior im Eigenschaftenbereich](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4\_FluidMoveBehaviorProperties\_Sample")  
  
 **Sehen Sie sich ein kurzes Video an \(nur in englischer Sprache verfügbar\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Blend\-Tipps: Einführung in die Verwendung von Verhaltensweisen Teil 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### Ereignisse  
 Für maximale Flexibilität behandeln Sie ein *Ereignis*. Sie müssen Code schreiben.  
  
 **Sehen Sie sich ein kurzes Video an \(nur in englischer Sprache verfügbar\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Fügen Sie ein Mausereignis hinzu](https://www.youtube.com/watch?v=2PMxAlb-x_E).