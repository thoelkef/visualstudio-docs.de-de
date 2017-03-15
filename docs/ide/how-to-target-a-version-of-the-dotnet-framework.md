---
title: 'Vorgehensweise: .NET Framework-Version als Ziel | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 50
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7ebf1dfaa3753f1a1908b0327e8ed938115f1f13
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Gewusst wie: .NET Framework-Version als Ziel
In diesem Dokument wird beschrieben, wie eine bestimmte .NET Framework-Version für ein Projekt gewählt wird und wie diese Zielversion in vorhandenen Visual Basic-, Visual C#- oder Visual F#-Projekten geändert werden kann.  
  
> [!IMPORTANT]
>  Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](http://msdn.microsoft.com/Library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **In diesem Thema**  
  
-   [Projekt für eine Zielversion erstellen](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Projekt für eine Zielversion erstellen  
 Wenn Sie ein Projekt erstellen, bestimmt die Version von .NET Framework, auf die Sie abzielen, die Vorlagen, die Sie verwenden können.  
  
> [!NOTE]
>  In den Express-Editionen von Visual Studio müssen Sie zuerst das Projekt erstellen und können dann erst die Zielversion ändern, wie unter [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) weiter unten in diesem Thema beschrieben.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>So richten Sie ein Projekt bei der Erstellung auf eine Zielversion aus  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Wählen Sie in der Liste oben im Dialogfeld **Neues Projekt** die gewünschte .NET Framework-Version für Ihr Projekt aus.  
  
    > [!NOTE]
    >  In der Regel wird nur eine .NET Framework-Version zusammen mit Visual Studio installiert. Wenn Sie eine andere Zielversion verwenden möchten, müssen Sie zunächst sicherstellen, dass diese installiert ist. Weitere Informationen finden Sie in der [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  In der Liste der installierten Vorlagen wählen Sie den Typ des Projekts aus, das Sie erstellen möchten, benennen das Projekt und wählen dann die Schaltfläche **OK**.  
  
     In der Liste der Vorlagen werden nur die Projekte angezeigt, die von der ausgewählten .NET Framework-Version unterstützt werden.  
  
##  <a name="bkmk_existing"></a> Ändern der Zielversion  
 Die folgenden Schritte zeigen, wie eine .NET Framework-Zielversion in einem vorhandenen Visual Basic-, Visual C#- oder Visual F#-Projekt geändert wird.  
  
#### <a name="to-change-the-targeted-version"></a>So ändern Sie die Zielversion  
  
1.  Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften** aus.  
  
     ![Visual Studio Eigenschaften des Projektmappen-Explorer](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](http://msdn.microsoft.com/Library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  Im linken Bereich des Fensters Eigenschaften wählen Sie die Registerkarte **Anwendung** aus.  
  
     ![Visual Studio, App-Eigenschaften, Registerkarte „Anwendung“](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Nachdem Sie eine Windows Store-App in Visual Studio&2013; erstellt haben, können Sie weder die Windows-Zielversion noch die .NET Framework-Zielversion ändern.  
  
3.  Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.  
  
4.  Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.  
  
     Das Projekt wird entladen. Wenn es erneut geladen wird, verwendet es die .NET Framework-Zielversion, die Sie soeben ausgewählt haben.  
  
    > [!NOTE]
    >  Sollte der Code Verweise auf eine .NET Framework-Version enthalten, die nicht die Zielversion ist, werden möglicherweise Fehlermeldungen angezeigt, wenn Sie den Code kompilieren oder ausführen. Um diese Fehler zu beheben, müssen Sie die Verweise ändern. Weitere Informationen finden Sie unter [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET Framework Multi-Targeting for ASP.NET Web Projects (.NET-Framework-Zielversionen für ASP.NET-Webprojekte)](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Konfigurieren von Projekten](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets](http://msdn.microsoft.com/Library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
