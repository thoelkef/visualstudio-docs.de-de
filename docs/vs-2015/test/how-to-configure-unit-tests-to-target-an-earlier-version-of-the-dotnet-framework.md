---
title: 'Vorgehensweise: Konfigurieren von Komponententests zur Ausrichtung auf eine frühere Version von .NET Framework | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fd212eb304e6cba022b067b8b432cf00fc3f87ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660538"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Gewusst wie: Konfigurieren von Komponententests zur Ausrichtung auf eine frühere Version von .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie in Microsoft Visual Studio ein Testprojekt erstellen, wird die neueste Version von .NET Framework standardmäßig als Ziel festgelegt. Wenn Sie ein Upgrade von Projekten aus früheren Versionen von Visual Studio durchführen, werden Projektupgrades darüber hinaus auf die neueste Version von .NET Framework durchgeführt. Durch Bearbeiten der Projekteigenschaften können Sie das Projekt auf frühere Versionen von .NET Framework explizit umleiten.

 Sie können Komponententestprojekte erstellen, die auf bestimmte Versionen von .NET Framework abzielen. Die Zielversion muss 3.5 oder höher sein und darf keine Clientversion sein. Visual Studio ermöglicht die folgende grundlegende Unterstützung für Komponententests, die auf bestimmte Versionen abzielen:

- Sie können Komponententestprojekte erstellen und sie auf eine bestimmte Version von .NET Framework leiten.

- Sie können Komponententests ausführen, die auf eine bestimmte Version von .NET Framework in Visual Studio auf Ihrem lokalen Computer abzielen.

- Sie können Komponententests ausführen, die mithilfe von „MSTest.exe“ über die Eingabeaufforderung auf eine bestimmte Version von .NET Framework abzielen.

- Sie können Komponententests auf einen Build-Agent als Teil eines Builds ausführen.

  **Testen von SharePoint-Anwendungen**

  Die oben genannten Funktionen helfen Ihnen auch beim Schreiben von Komponenten- und Integrationstest für SharePoint-Anwendungen, die Visual Studio verwenden. [!INCLUDE[crabout](../includes/crabout-md.md)] Informationen zum Entwickeln von SharePoint-Anwendung mithilfe von Visual Studio finden Sie unter [Erstellen von SharePoint-Lösungen](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [Erstellen und Debuggen von SharePoint-Lösungen](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) und [Überprüfen und Debuggen von SharePoint-Code](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).

  **Einschränkungen**

  Die folgenden Einschränkungen gelten, wenn Sie Ihre Testprojekte zum Verwenden von früheren .NET Framework-Versionen umleiten:

- In .NET Framework 3.5 wird die Festlegung von Zielversionen für Testprojekte unterstützt, die nur Komponententests enthalten. .NET Framework 3.5 unterstützt keine anderen Testtypen, z.B. Tests der programmierten UI oder Auslastungstests. Die Umleitung ist für Testtypen, die keine Komponententests sind, blockiert.

- Ausführung von Tests, die auf eine frühere Version von .NET Framework abzielen, ist nur im standardmäßigen Hostadapter unterstützt. Es wird nicht im Hostadapter „ASP.NET“ unterstützt. ASP.NET-Anwendungen, die unter dem Kontext „ASP.NET Development Server“ ausgeführt werden müssen, müssen mit der aktuellen Version von .NET Framework kompatibel sein.

- Die Unterstützung der Datensammlung ist deaktiviert, wenn Sie Tests ausführen, die die Festlegung von Zielversionen in .NET Framework 3.5 unterstützen. Sie können Code Coverage mithilfe der Visual Studio-Befehlszeilentools ausführen.

- Komponententests, die .NET Framework 3.5 verwenden, können nicht auf einem Remotecomputer ausgeführt.

- Sie können keine Komponententests zu früheren Clientversionen des Frameworks leiten.

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Umleiten zu einer bestimmten Version von .NET Framework für Visual Basic-Komponententestprojekte

1. Erstellen Sie ein neues Visual Basic-Komponententestprojekt. Wählen Sie im Menü **Datei** die Option **Neu** und anschließend **Projekt** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Klicken Sie unter **Installierte Vorlagen**auf **Visual Basic**. Wählen Sie **Test** und anschließend die Vorlage **Testprojekt** aus.

3. Geben Sie im Textfeld **Name** einen Namen für das Projekt ein, und klicken Sie anschließend auf **OK**.

4. Wählen Sie im Projektmappen-Explorer **Eigenschaften** unter dem Kontextmenü des neuen Visual Basic-Testprojekts aus.

     Die Eigenschaften für Ihr Visual Basic-Testprojekt werden angezeigt.

5. Klicken sie auf der Registerkarte **Kompilieren** auf **Erweiterte Kompilierungsoptionen**, wie es in der folgenden Abbildung gezeigt wird.

     ![Erweiterte Kompilierungsoptionen](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")

6. Verwenden Sie die Dropdownliste **Zielframework (alle Konfigurationen)** , um das Zielframework auf **.NET Framework 3.5** oder eine höhere Version zu ändern, wie es im Beispiel B der folgenden Abbildung gezeigt wird. Sie sollten keine Clientversion angeben.

     ![Dropdown&#45;Liste für das Ziel Framework](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Umleiten zu einer bestimmten Version von .NET Framework für Visual C#-Komponententestprojekte

1. Erstellen Sie ein neues Visual C#-Komponententestprojekt. Wählen Sie im Menü **Datei** die Option **Neu** und anschließend **Projekt** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Klicken Sie unter **Installierte Vorlagen**auf **Visual C#** . Wählen Sie **Test** und anschließend die Vorlage **Testprojekt** aus.

3. Geben Sie im Textfeld **Name** einen Namen für Ihr Visual C#-Testprojekt ein, und klicken Sie anschließend auf **OK**.

4. Wählen Sie im Projektmappen-Explorer **Eigenschaften** unter dem Kontextmenü des neuen Visual C#-Testprojekts aus.

     Die Eigenschaften für Ihr Visual C#-Testprojekt werden angezeigt.

5. Klicken Sie zum Ändern des Zielframeworks in der Registerkarte **Anwendung** auf **Zielframework** und wählen Sie anschließend von der Dropdownliste **.NET Framework 3.5** oder eine spätere Version aus, wie es in der folgenden Abbildung gezeigt wird. Sie sollten keine Clientversion angeben.

     ![Dropdown&#45;Liste für das Ziel Framework](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Umleiten zu einer bestimmten Version von .NET Framework für C++/CLI-Komponententestprojekte

1. Erstellen Sie ein neues C++-Komponententestprojekt. Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

    > [!WARNING]
    > Sie müssen die entsprechende Version von Visual Studio verwenden, um C++/CLI-Komponententestprojekte für eine frühere Version von .NET Framework für C++ zu erstellen. Sie müssen Service Pack 1 von [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] und [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] installieren, um z.B. auf .NET Framework 3.5 abzuleiten.

2. Klicken Sie unter **Installierte Vorlagen**auf **Visual C ++** . Wählen Sie **Test** und anschließend die Vorlage **Testprojekt** aus.

3. Geben Sie im Textfeld **Name** einen Namen für Ihr Visual C++-Testprojekt ein, und klicken Sie anschließend auf **OK**.

4. Wählen Sie im Projektmappen-Explorer **Projekt entladen** von dem neuen Visual C++-Testprojekt.

5. Wählen Sie im Projektmappen-Explorer das entladene Visual C++-Testprojekt, und wählen Sie anschließend **\<Projektname> .vcxproj bearbeiten**.

     Die VCXPROJ-Datei wird im Editor geöffnet.

6. Legen Sie `TargetFrameworkVersion` auf Version 3.5 oder höher in `PropertyGroup`, die als `"Globals"` bezeichnet wird, fest. Sie sollten keine Clientversion angeben:

    ```
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>

    ```

7. Speichern und schließen Sie die VCXPROJ-Datei.

8. Wählen Sie im Projektmappen-Explorer **Projekt erneut laden** unter dem Kontextmenü des neuen Visual C#-Testprojekts aus.

## <a name="see-also"></a>Siehe auch
 [Erstellen und Ausführen von Komponenten Tests für vorhandenen Code erstellen von](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [SharePoint-Lösungen erstellen](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [und Debuggen von SharePoint-Lösungen](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [Erweiterte Compilereinstellungen (Dialog Feld) Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
