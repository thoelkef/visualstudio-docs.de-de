---
title: "Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für UWP-Apps | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: ghogen
ms.workload: uwp
author: gewarren
ms.openlocfilehash: 82ba9f9419964d9c626a81f78cf7f8ccace57320
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-and-running-unit-tests-for-uwp-apps"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für UWP-Apps
Visual Studio bietet Unterstützung für Komponententests verwalteter [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -Anwendungen und enthält Komponententest-Bibliotheksvorlagen für Visual C#, Visual Basic und Visual C++.  
  
> [!TIP]
>  Weitere Informationen zum Entwickeln von [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps finden Sie unter [Erste Schritte mit UWP-Apps](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Visual Studio stellt die folgende Funktionalität für Unittests bereit:  
  
-   [Erstellen eines Komponententestprojekts](#CreateAndRunUnitTestWin8Tailored_Create)  
  
-   [Bearbeiten des Manifests für das Komponententestprojekt](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
-   [Codieren des Komponententests](#CreateAndRunUnitTestWin8Tailored_Code)  
  
-   [Ausführen von Komponententests](#CreateAndRunUnitTestWin8Tailored_Run)  
  
 Im folgenden sind Schritte zur Erstellung, zum Lauf und zum Debugging von Komponententests für verwaltete Windows 8 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps beschrieben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Erstellen eines Komponententestprojekts  
  
#### <a name="to-create-a-unit-test-project-for-a-uwp-app"></a>Erstellen eines Komponententestprojekts für eine UWP-App  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt**aus.  
  
     Daraufhin wird das Dialogfeld "Neues Projekt" angezeigt.  
  
2.  Wählen Sie unter Vorlagen die Programmiersprache aus, in der Sie den Komponententest erstellen möchten, und wählen Sie dann die zugeordnete [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -Komponententestbibliothek aus. Wählen Sie beispielsweise **Visual C#** aus, und wählen Sie dann **Windows Universal** gefolgt von **Komponententestbibliothek (Universal Windows)** aus.  
  
    > [!NOTE]
    >  Visual Studio enthält Komponententest-Bibliotheksvorlagen für Visual C#, Visual Basic und Visual C++.  
  
3.  (Optional) Geben Sie im Textfeld **Name** den Namen ein, den Sie für das [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Komponententestprojekt verwenden möchten.  
  
4.  (Optional) Ändern Sie den Pfad, unter dem Sie das Projekt erstellen möchten, indem Sie ihn im Textfeld **Speicherort** eingeben, oder klicken Sie auf die Schaltfläche **Durchsuchen** .  
  
5.  (Optional) Geben Sie im Textfeld **Projektmappe** den Namen ein, den Sie für die Projektmappe verwenden möchten.  
  
6.  Vergewissern Sie sich, dass die Option **Projektmappenverzeichnis erstellen** ausgewählt ist, und klicken Sie auf **OK** .  
  
     ![Angepasste Komponententestbibliothek](../test/media/unit_test_win8_1.png "Unit_Test_Win8_1")  
  
     Der Projektmappen-Explorer wird mit dem neuen [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Komponententestprojekt ausgefüllt, und der Code-Editor zeigt den Standardkomponententest, UnitTest1, an.  
  
     ![Neues angepasstes Komponententestprojekt](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Bearbeiten des Manifests für das Komponententestprojekt  
 Möglicherweise müssen Sie das Manifest für das Komponententestprojekt bearbeiten, um die erforderlichen Funktionen für die Ausführung der App bereitzustellen.  
  
#### <a name="to-edit-the-unit-test-projects-uwp-application-manifest-file"></a>Bearbeiten der UWP-Anwendungsmanifestdatei für das Komponententestprojekt  
  
1.  Klicken Sie im Projektmappen-Explorer im neuen [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -Komponententestprojekt mit der rechten Maustaste auf die Datei Package.appxmanifest und wählen Sie **Öffnen**aus.  
  
     Daraufhin wird der Manifest-Designer für die Bearbeitung angezeigt.  
  
2.  Wählen Sie im Manifest-Designer die Registerkarte **Funktionen** aus.  
  
3.  Wählen Sie in der **Funktionen**-Liste die Funktionen, über die die getestete Komponente verfügen soll, und den für diese Tests erforderlichen Code aus. Aktivieren Sie beispielsweise das Kontrollkästchen **Internet** , wenn die Komponente, die getestet werden soll, und der Code Zugriff auf das Internet benötigen.  
  
    > [!NOTE]
    >  Die ausgewählten Funktionen sollten nur Funktionen enthalten, die für die ordnungsgemäße Durchführung des [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -Komponententests erforderlich sind. Sie sollten niemals Funktionen auswählen, die nicht Teil der zu testenden [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App sind. Die Funktionen sollten im Allgemeinen eine Untergruppe der Funktionen sein, die für die getestete [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App angegeben werden.  
  
     Weitere Informationen zum Manifest-Designer finden Sie unter [Konfigurieren eines Windows 8.1-App-Pakets mit dem Manifest-Designer](http://msdn.microsoft.com/Library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Komponententestmanifest](../test/media/unit_test_win8_.png "Unit_Test_Win8_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Codieren des Komponententests  
  
#### <a name="to-code-the-unit-test-for-a-uwp-app"></a>Schreiben von Code für den Komponententest einer UWP-App  
  
1.  Bearbeiten Sie im Code-Editor den Komponententest und fügen Sie die Bestätigungs- und Logikanforderungen für den Test hinzu.  
  
     Weitere Informationen finden Sie unter [Verwenden von Assert-Klassen](http://go.microsoft.com/fwlink/?LinkID=224991) in der MSDN Library.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Ausführen von Komponententests  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>So erstellen Sie die Projektmappe und führen den Komponententest mit dem Komponententest-Explorer aus  
  
1.  Wählen Sie im Menü **Test** den Punkt **Windows**und dann **Test-Explorer**aus.  
  
     Daraufhin wird der Komponententest-Explorer ohne Ihren Test angezeigt.  
  
2.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
     Der Komponententest wird jetzt aufgeführt.  
  
    > [!NOTE]
    >  Sie müssen die Projektmappe erstellen, um die Liste der Komponententests im Komponententest-Explorer zu aktualisieren.  
  
    > [!WARNING]
    >  Bekanntes Visual Studio-Problem: Sie müssen den Komponententest-Explorer vor dem Erstellen des Testprojekts öffnen.  
  
3.  Wählen Sie im Test-Explorer den Komponententest aus, den Sie erstellt haben.  
  
    > [!TIP]
    >  Der Test-Explorer stellt neben **Quelle:**einen Link zum Quellcode bereit.  
  
4.  Wählen Sie **Alle ausführen** aus.  
  
     ![Komponententest-Explorer &#45; Komponententest ausführen](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    >  Sie können mehr als einen der im Komponententest-Explorer aufgeführten Komponententests auswählen und per Rechtsklick **Ausgewählte Tests ausführen**auswählen.  
    >   
    >  Außerdem können Sie die Optionen **Ausgewählte Tests debuggen**, **Test öffnen**und **Eigenschaften** auswählen.  
    >   
    >  ![Komponententest-Explorer &#45; Komponententest-Kontextmenü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Der Komponententest läuft. Nach Abschluss zeigt der Komponententest-Explorer den Teststatus und die verstrichene Zeit an und stellt einen Link zur Quelle bereit.  
  
     ![Komponententest-Explorer &#45; Test abgeschlossen](../test/media/unit_test_win8_unittestexplorer_done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="videos"></a>Videos  
 [Channel 9: Unit testing your UWP apps built using XAML (Channel 9: Durchführen von Komponententests für Ihre mit XAML erstellten UWP-Apps)](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Foren  
 [Visual Studio-Komponententest](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>MSDN Library  
 [MSDN Library - Creating and Running Unit Tests for Existing Code (Visual Studio 2010) (MSDN Library – Erstellen und Ausführen von Komponententests für vorhandenen Code (Visual Studio 2010))](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>Siehe auch  
 [Testen von UWP-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Erstellen und Testen einer UWP-App mithilfe von Team Foundation Build](http://msdn.microsoft.com/Library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
