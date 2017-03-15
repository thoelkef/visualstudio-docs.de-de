---
title: "Anordnen eines Benutzersteuerelements in einem Toolfenster | Microsoft Docs"
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
  - "Toolfenster, Hinzufügen von Benutzersteuerelementen"
  - "Benutzersteuerelemente [Visual Studio SDK], Hinzufügen zu Toolfenstern"
  - "Benutzersteuerelemente [Visual Studio]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Anordnen eines Benutzersteuerelements in einem Toolfenster
In dieser exemplarische Vorgehensweise wird veranschaulicht, wie ein Benutzersteuerelement einem Toolfenster hinzugefügt wird.  
  
 Ein Benutzersteuerelement ist eine Sammlung von Windows\-Steuerelementen, die in einem einzigen Steuerelement kombiniert sind. Um einem Toolfenster ein Benutzersteuerelement hinzuzufügen, müssen Sie lediglich dafür sorgen, dass das Benutzersteuerelement in der **Toolbox** angezeigt wird. Das Benutzersteuerelement, das in dieser exemplarischen Vorgehensweise verwendet wird, ist das Uhren\-Steuerelement, das in [Exemplarische Vorgehensweise: Erstellen eines zusammengesetzten Steuerelements mit Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md) entwickelt wurde.  
  
## Vorbereitungsmaßnahmen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Erstellen des Benutzersteuerelements  
  
1.  Führen Sie die Schritte in [Exemplarische Vorgehensweise: Erstellen eines zusammengesetzten Steuerelements mit Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md) aus, um das Uhren\-Steuerelement zu erstellen. Erstellen Sie nicht das Wecker\-Steuerelement.  
  
> [!NOTE]
>  Für die folgenden Schritte wird davon ausgegangen, dass Sie dem Uhren\-Steuerelement den Namen `ctlClock` gegeben haben.  
  
## Erstellen einer Toolfenstererweiterung  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `MyToolWindowPackageUC`, das ein Toolfenster namens `MyToolWindow` hat. Wenn Sie hierzu Unterstützung benötigen, lesen Sie [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Hinzufügen des Benutzersteuerelements  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Projektmappe **MyToolWindowPackageUC**, zeigen Sie auf **Hinzufügen**, und klicken Sie anschließend auf **Vorhandenes Projekt**.  
  
2.  Öffnen Sie im Dialogfeld **Vorhandenes Projekt hinzufügen** das Projekt „ctlClockLib“, und wählen Sie die Projektdatei „ctlClock.lib.csproj“ aus. Klicken Sie auf **OK**. Dadurch wird das Benutzersteuerelement aktiviert, das Sie im Designer verwenden können.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf „MyToolWindowControl.cs“, und wählen Sie **Ansicht\-Designer** aus. Hierdurch wird der Forms\-Designer geöffnet, in dem das generierte Steuerelement für das Toolfenster angezeigt wird.  
  
4.  Öffnen Sie die **Toolbox**, suchen Sie nach dem Abschnitt mit der Bezeichnung **ctlClockLib Components**, und doppelklicken Sie auf das **ctlClock**\-Steuerelement in diesem Abschnitt, um das Steuerelement dem Formular hinzuzufügen. Sobald Sie die **Toolbox** ausblenden, sollten Sie eine Zeitanzeige in Ihrem Toolfensterformular sehen.  
  
5.  Wählen Sie im Designer das Uhren\-Steuerelement aus, das Sie soeben hinzugefügt haben, und ändern Sie die **Anker** Eigenschaft in **Oben**.  
  
6.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den ctlClockLib\-Projektknoten, und klicken Sie dann auf **Eigenschaften**.  
  
7.  Wählen Sie auf der Registerkarte **Signierung** die Option **Assembly signieren** aus. Klicken Sie im Feld **Schlüsseldatei mit starkem Namen auswählen** auf **\<Durchsuchen\>**, und navigieren Sie zu der Datei „key.snk“ m **MyToolWindowPackageUC**\-Projektordner.  
  
8.  Kompilieren Sie das Programm, und vergewissern Sie sich, dass keine Fehler vorliegen. In diesem Schritt werden das VSPackage und dessen Toolfenster für Visual Studio registriert.  
  
9. Drücken Sie F5, um eine Instanz von Visual Studio in der experimentellen Struktur zu öffnen.  
  
10. Zeigen Sie im experimentellen Visual Studio im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **MyToolWindow**. Dadurch wird Ihr Toolfenster angezeigt, das eine aktive Zeitanzeige hat.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines zusammengesetzten Steuerelements mit Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)