---
title: Erstellen eines Komponententestprojekts | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 8
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: a5d365df024b8847fbbd9df4be1aa7053f6f7634
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen
Komponententests spiegeln häufig die Struktur des getesteten Codes. Angenommen, für jedes Codeprojekt im Produkt wird ein Komponententestprojekt erstellt. Das Testprojekt kann sich in der gleichen Projektmappe wie der Produktionscode oder in einer separaten Projektmappe befinden. In einer Projektmappe können sich mehrere Komponententestprojekte befinden.  
  
> [!NOTE]
>  Der Speicherort von Komponententests für nativen Code und die Testprojektstruktur können sich von in diesem Thema beschriebenen Struktur unterscheiden. Weitere Informationen finden Sie unter [Hinzufügen von Komponententests zu vorhandenen C++-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)  
  
## <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Komponententestprojekt  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** und dann **Projekt** aus (Tastatur: STRG+UMSCHALT+N).  
  
2.  Erweitern Sie im Dialogfeld „Neues Projekt“ den Knoten **Installiert**, wählen Sie die Sprache aus, die Sie für das Testprojekt verwenden möchten, und wählen Sie anschließend **Test** aus.  
  
3.  Wenn Sie ein Microsoft-Komponententest-Framework verwenden möchten, wählen Sie aus der Liste der Projektvorlagen **Komponententestprojekt** aus. Wählen Sie andernfalls die Projektvorlage des Komponententest-Frameworks aus, das Sie verwenden möchten. Testen Sie das Kontenprojekt aus unserem Beispiel, und nennen Sie es „AccountsTests“.  
  
4.  Fügen Sie Ihrem Komponententestprojekt einen Verweis auf den zu testenden Code hinzu.  So erstellen Sie den Verweis auf ein Codeprojekt in der gleichen Projektmappe:  
  
    1.  Wählen Sie das Projekt im Projektmappen-Explorer aus.  
  
    2.  Wählen Sie im Menü **Projekt** den Eintrag **Verweis hinzufügen...** aus.  
  
    3.  Öffnen Sie im Dialogfeld „Verweis-Manager“ den Knoten **Projektmappe**, und wählen Sie **Projekte** aus. Wählen Sie den Namen des Codeprojekts aus, und schließen Sie das Dialogfeld.  
  
5.  Wenn sich der zu testende Code an einem anderen Speicherort befindet, finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md) weitere Informationen zum Hinzufügen von Verweisen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 **Schreiben von Komponententests**  
  
 Siehe eines der folgenden Themen:  
  
-   [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Schreiben von Komponententests für C/C++ mit dem Microsoft-Unittest-Framework für C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
 **Ausführen von Komponententests**  
  
 [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)

