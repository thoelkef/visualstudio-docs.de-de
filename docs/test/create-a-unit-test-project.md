---
title: "Ein Komponententestprojekt erstellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Ein Komponententestprojekt erstellen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Komponententests spiegeln häufig die Struktur der getesteten Code. Beispielsweise würde ein Komponententestprojekt für jedes Codeprojekt im Produkt erstellt werden. Das Testprojekt kann in der gleichen Projektmappe wie Produktionscode, oder es kann in einer separaten Projektmappe. Sie können mehrere Projekte in einer Projektmappe testen Einheit haben.  
  
> [!NOTE]
>  Der Speicherort des Komponententests für systemeigenen Code testet und der Test-Projektstruktur kann anders als die Struktur, die in diesem Thema beschrieben wird. Weitere Informationen finden Sie unter [Hinzufügen von Komponententests zu vorhandenen C++-Anwendung](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Testprojekt hinzu:  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** und dann **Projekt** aus (Tastatur: STRG+UMSCHALT+N).  
  
2.  Erweitern Sie im Dialogfeld Neues Projekt die **installierte** Knoten, wählen Sie die Sprache, die Sie verwenden möchten, verwenden Sie für das Testprojekt, und wählen Sie dann **Testen**.  
  
3.  Wenn Sie ein Microsoft-Komponententest-Framework verwenden möchten, wählen Sie aus der Liste der Projektvorlagen **Komponententestprojekt** aus. Wählen Sie andernfalls die Projektvorlage des Komponententest-Frameworks aus, das Sie verwenden möchten. Zum Testen des Projekts Konten diesem Beispiel nennen Sie das Projekt AccountsTests.  
  
4.  Fügen Sie einen Verweis auf den Code unter Test in das Komponententestprojekt.  Hier ist den Verweis auf ein Projekt mit Code in der gleichen Projektmappe zu erstellen:  
  
    1.  Wählen Sie das Projekt im Projektmappen-Explorer aus.  
  
    2.  Auf der **Projekt** Menü wählen **Verweis hinzufügen**.  
  
    3.  Klicken Sie im Dialogfeld Verweis-Manager öffnen der **Lösung** Knoten, und wählen Sie **Projekte**. Überprüfen Sie den Namen des Codeprojekts, und schließen Sie das Dialogfeld zu.  
  
5.  Wenn der Code, der zu testenden an einem anderen Speicherort ist, finden Sie unter [Verwalten Verweise in einem Projekt](../ide/managing-references-in-a-project.md) Informationen zum Hinzufügen von verweisen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 **Schreiben von Komponententests**  
  
 Finden Sie in den folgenden Abschnitten:  
  
-   [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Schreiben von Komponententests für C/C++ mit dem Microsoft-Komponententestframework für C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
 **Ausführen von Komponententests**  
  
 [Ausführen von Komponententests mit Test-Explorer](../test/run-unit-tests-with-test-explorer.md)