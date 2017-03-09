---
title: "Gewusst wie: .NET Framework-Version als Ziel | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ansteuern von .NET Framework-Version [Visual Studio]"
  - "Versionen [Visual Studio], Ansteuern von .NET Framework-Version"
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 50
caps.handback.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: .NET Framework-Version als Ziel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird beschrieben, wie eine bestimmte .NET Framework\-Version für ein Projekt gewählt wird und wie diese Zielversion in vorhandenen Visual Basic\-, Visual C\#\- oder Visual F\#\-Projekten geändert werden kann.  
  
> [!IMPORTANT]
>  Weitere Informationen zum Ändern der Zielversion für C\+\+\-Projekte finden Sie unter [Gewusst wie: Ändern des Zielframeworks und des Plattformtoolsets](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md).  
  
 **In diesem Thema**  
  
-   [Projekt für eine Zielversion erstellen](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Projekt für eine Zielversion erstellen  
 Wenn Sie ein Projekt erstellen, bestimmt die Version von .NET Framework, auf die Sie abzielen, die Vorlagen, die Sie verwenden können.  
  
> [!NOTE]
>  In den Express\-Editionen von Visual Studio müssen Sie zuerst das Projekt erstellen und können dann erst die Zielversion ändern, wie unter [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) weiter unten in diesem Thema beschrieben.  
  
#### So richten Sie ein Projekt bei der Erstellung auf eine Zielversion aus  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Wählen Sie in der Liste oben im Dialogfeld **Neues Projekt** die gewünschte .NET Framework\-Version für Ihr Projekt.  
  
    > [!NOTE]
    >  In der Regel wird nur eine .NET Framework\-Version zusammen mit Visual Studio installiert.  Wenn Sie eine andere Zielversion verwenden möchten, müssen Sie zunächst sicherstellen, dass diese installiert ist.  Weitere Informationen finden Sie in der [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  In der Liste der installierten Vorlagen wählen Sie den Typ des Projekts, das Sie erstellen möchten, benennen das Projekt und wählen dann die Schaltfläche **OK**.  
  
     In der Liste der Vorlagen werden nur die Projekte angezeigt, die von der ausgewählten .NET Framework\-Version unterstützt werden.  
  
##  <a name="bkmk_existing"></a> Ändern der Zielversion  
 Die folgenden Schritte zeigen, wie eine .NET Framework\-Zielversion in einem vorhandenen Visual Basic\-, Visual C\#\- oder Visual F\#\-Projekt geändert wird.  
  
#### So ändern Sie die Zielversion  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften**.  
  
     ![Visual Studio Eigenschaften des Projektmappen&#45;Explorer](../ide/media/vs_slnexplorer_properties.png "vs\_slnExplorer\_Properties")  
  
    > [!IMPORTANT]
    >  Weitere Informationen zum Ändern der Zielversion für C\+\+\-Projekte finden Sie unter [Gewusst wie: Ändern des Zielframeworks und des Plattformtoolsets](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md).  
  
2.  Im linken Bereich des Fensters "Eigenschaften" wählen Sie die Registerkarte **Anwendung**.  
  
     ![Visual Studio, App&#45;Eigenschaften, Registerkarte "Anwendung"](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs\_slnExplorer\_Properties\_ApplicationTab")  
  
    > [!NOTE]
    >  Nachdem Sie eine Windows Store\-App in Visual Studio 2013 erstellt haben, können Sie weder die Windows\-Zielversion noch die .NET Framework\-Zielversion ändern.  
  
3.  Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.  
  
4.  Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.  
  
     Das Projekt wird entladen.  Wenn es erneut geladen wird, verwendet es die .NET Framework\-Zielversion, die Sie soeben ausgewählt haben.  
  
    > [!NOTE]
    >  Sollte der Code Verweise auf eine .NET Framework\-Version enthalten, die nicht die Zielversion ist, werden möglicherweise Fehlermeldungen angezeigt, wenn Sie den Code kompilieren oder ausführen.  Um diese Fehler zu beheben, müssen Sie die Verweise ändern.  Weitere Informationen finden Sie unter [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## Siehe auch  
 [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)   
 [Gewusst wie: Ändern des Zielframeworks und des Plattformtoolsets](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)