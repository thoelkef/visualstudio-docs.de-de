---
title: Erster Einblick in die Bereitstellung
description: Erfahren Sie, wie Sie Apps aus Visual Studio bereitstellen können.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 006ecdffd7b109c32f7063fee5f454e43c6c4597
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806926"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Ein erster Einblick in die Bereitstellung in Visual Studio

Wenn Sie eine Anwendung, einen Dienst oder eine Komponente bereitstellen, verteilen Sie diese für die Installation auf anderen Computern, Geräten, Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen. (Viele App-Typen unterstützen andere Bereitstellungstools, welche hier nicht beschrieben werden, z. B. das Tool zur Bereitstellung der Befehlszeile.)

Sehen Sie sich die Schnellstarts und Tutorials an, um ausführliche Anweisungen für die Bereitstellung anzuzeigen. Eine Übersicht der Bereitstellungsoptionen finden Sie unter [Welche Optionen für die Veröffentlichung sind für mich geeignet?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Bereitstellen in einem lokalen Ordner

Die Bereitstellung in einem lokalen Ordner wird normalerweise zum Testen verwendet oder um eine Stagingbereitstellung zu beginnen, in der zur endgültigen Bereitstellung ein anders Tool verwendet wird.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** und **.NET Core**: Verwenden Sie die Option „Veröffentlichen“, um eine Bereitstellung in einem lokalen Ordner durchzuführen. Welche Optionen genau verfügbar sind, hängt von Ihrem App-Typ ab. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, und wählen Sie **Veröffentlichen** aus. (Wenn Sie noch keine Veröffentlichungsprofile konfiguriert haben, klicken Sie auf **Neues Profil erstellen**.) Wählen Sie anschließend **Ordner** aus. Weitere Informationen finden Sie unter [Bereitstellen in einem lokalen Ordner](quickstart-deploy-to-local-folder.md).

    ![„Veröffentlichen“ auswählen](../deployment/media/quickstart-publish.png)

- **Windows-Desktop:** Sie können eine Windows-Desktopanwendung mit der ClickOnce-Bereitstellung in einem Ordner veröffentlichen. Benutzer können die Anwendung mit einem einzelnen Mausklick installieren. Weitere Informationen finden Sie unter [Bereitstellen einer Desktop-App mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# und Visual Basic). Informationen zu C++/CLI finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Veröffentlichen in Azure

- **ASP.NET**, **ASP.NET Core**, **Python** und **Node.js:** Mithilfe einer der folgenden Methoden können Sie Apps in Azure App Service oder Azure App Service Linux (mit Containern) veröffentlichen.

  - Verwenden Sie Azure DevOps mit [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops) für die kontinuierliche (oder automatisierte) Bereitstellung von Apps.

  - Verwenden Sie das Tool zum **Veröffentlichen** in Visual Studio für die einmalige (oder manuelle) Bereitstellung von Apps.

  Für Bereitstellungen die eine individuellere Konfiguration des Servers ermöglichen, können Sie das Tool zum **Veröffentlichen** auch zum Bereitstellen von Apps in einem virtuellen Azure-Computer verwenden.

  Klicken Sie zur Verwendung des Tools zum **Veröffentlichen** mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, und wählen Sie **Veröffentlichen** aus. (Wenn Sie zuvor Veröffentlichungsprofile konfiguriert haben, klicken Sie auf **Neues Profil erstellen**.) Wählen Sie im Dialogfeld „Veröffentlichen“ entweder **App Service** oder **Azure Virtual Machines** aus, und führen Sie dann die Konfigurationsschritte aus.

  ![Azure App Service auswählen](../deployment/media/quickstart-publish-azure.png "Azure App Service auswählen")

  Ab Visual Studio 2017, Version 15.7 können Sie ASP.NET Core-Apps in **App Service für Linux** bereitstellen.

  Weitere Informationen zu Python-Apps finden Sie unter [Python: Veröffentlichen in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Eine kurze Einführung finden Sie unter [Veröffentlichen in Azure](quickstart-deploy-to-azure.md) und [Veröffentlichen unter Linux](quickstart-deploy-to-linux.md). Lesen Sie auch [Veröffentlichen einer ASP.NET Core-App in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Weitere Informationen zur Bereitstellung mit Git finden Sie unter [Continuous Deployment von ASP.NET Core in Azure mit Git](/aspnet/core/publishing/azure-continuous-deployment).

  Weitere Informationen zum Importieren eines Veröffentlichungsprofils aus Azure App Service in Visual Studio, finden Sie unter [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Wenn Sie noch kein Azure-Konto besitzen, können Sie sich [hier registrieren](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Veröffentlichen im Web oder Bereitstellen zur Netzwerkfreigabe

- **ASP.NET**, **ASP.NET Core**, **Node.js** und **Python:** Zur Bereitstellung auf einer Website mithilfe von FTP oder Web Deploy können Sie die Option „Veröffentlichen“ verwenden. Weitere Informationen finden Sie unter [Bereitstellen auf einer Website](quickstart-deploy-to-a-web-site.md).

    Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**. (Wenn Sie zuvor Veröffentlichungsprofile konfiguriert haben, klicken Sie auf **Neues Profil erstellen**.) Wählen Sie im Tool „Veröffentlichen“ die gewünschte Option aus, und führen Sie die Konfigurationsschritte aus.

    ![Auswählen von IIS, FTP, usw.](../deployment/media/quickstart-publish-iis-ftp.png)

    Weitere Informationen zum Importieren eines Veröffentlichungsprofils in Visual Studio, finden Sie unter [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Es gibt noch viele weitere Möglichkeiten, ASP.NET-Anwendungen und -Dienste bereitzustellen. Weitere Informationen finden Sie unter [Bereitstellen von ASP.NET-Webanwendungen und -Diensten](/aspnet/mvc/overview/deployment/).

- **Windows Desktop**: Mit der ClickOnce-Bereitstellung können Sie eine Windows-Desktopanwendung auf einem Webserver oder in einer Netzwerk-Dateifreigabe veröffentlichen. Benutzer können die Anwendung mit einem einzelnen Mausklick installieren. Weitere Informationen finden Sie unter [Bereitstellen einer Desktop-App mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# und Visual Basic). Informationen zu C++/CLI finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Veröffentlichen im Microsoft Store

Sie können aus Visual Studio App-Pakete zur Bereitstellung im Microsoft Store erstellen.

- **UWP:** Sie können Ihre App packen und mithilfe von Menüelementen bereitstellen. Weitere Informationen finden Sie unter [Packen einer UWP-App mit Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Erstellen eines App-Pakets](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows-Desktop:** Eine Bereitstellung im Microsoft Store ist ab Version 15.4 in Visual Studio 2017 möglich. Erstellen Sie hierzu als Erstes ein Paketerstellungsprojekt für Windows-Anwendungen. Weitere Informationen finden Sie unter [Packen einer Desktop-App für den Microsoft Store](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

    ![Packen einer Desktop-App](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>Bereitstellen von .NET-Paketen in NuGet.org

Zum Bereitstellen von gepacktem Code in „Paketen“, die kompilierten Code (in Form von DLLs) sowie weitere Inhalte enthalten, die von den Projekten benötigt werden, die diese Pakete nutzen, können Sie das NuGet-Paket in Visual Studio erstellen und den endgültigen Bereitstellungsbefehl in einem Befehlszeilenschnittstellentool ausgeben.

- [Erstellen und Veröffentlichen eines .NET Standard-Pakets](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Erstellen und Veröffentlichen eines .NET Framework-Pakets](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Bereitstellen für ein Gerät (UWP)

Wenn Sie eine UWP-App zum Testen auf einem Gerät bereitstellen, lesen Sie mehr dazu unter [Ausführen von UWP-Apps auf einem Remotecomputer in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Erstellen eines Installationspakets (Windows-Desktop)

Wenn Sie eine komplexere Installation einer Desktop-Anwendung benötigen als [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) sie bietet, können Sie ein Windows Installer-Paket (MSI- oder EXE-Installationsdatei) oder einen benutzerdefinierten Bootstrapper erstellen.

- Mithilfe der [WiX-Toolseterweiterung](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset) kann ein MSI-basiertes Installationspaket erstellt werden. Dabei handelt es sich um ein Befehlszeilentoolset.

   ::: moniker range=">=vs-2019"
   Laden Sie sich für Visual Studio 2019 die [WiX-Toolseterweiterung für Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension) herunter.
   ::: moniker-end

- MSI- oder EXE-Installer-Pakete können mithilfe von [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) von Flexera Software erstellt werden. InstallShield kann mit Visual Studio 2017 und höheren Versionen verwendet werden (Community Edition wird nicht unterstützt). Beachten Sie, dass InstallShield Limited Edition nicht mehr in Visual Studio enthalten ist und in Visual Studio 2017 und höheren Versionen nicht unterstützt wird. Bei Fragen zur zukünftigen Verfügbarkeit wenden Sie sich an [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio).

- MSI- oder EXE-Installer-Pakete können mithilfe eines Setupprojekts (vdproj) erstellt werden. Installieren Sie die [Projekterweiterung für Visual Studio-Installer](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview), um diese Option zu verwenden.

- Sie können die erforderlichen Komponenten für Desktopanwendungen auch installieren, indem Sie ein generisches Installationsprogramm konfigurieren, das als Bootstrapper bezeichnet wird. Weitere Informationen finden Sie unter [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Bereitstellen in Testumgebung

Stellen Sie die Anwendungen in virtuellen Umgebungen bereit, um ausgereiftere Entwicklungs- und Testvorgänge zu ermöglichen. Weitere Informationen finden Sie unter [Testen in einer Laborumgebung](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Continuous Deployment

Sie können Azure Pipelines verwenden um Continuous Deployment (kontinuierliche Bereitstellung) für Ihre App zu ermöglichen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) und [Bereitstellen in Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deploy-a-sql-database"></a>Bereitstellen einer SQL-Datenbank

- [Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts (SQL Server Data Tools [SSDT])](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Bereitstellen eines Analysis Services-Projekts (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Bereitstellen von Integration Services-Projekten und -Paketen (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Erstellen und Bereitstellen in einer lokalen Datenbank](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Bereitstellung für andere App-Typen

| App-Typ | Bereitstellungsszenario | Link |
| --- | --- | --- |
| **Office-App** | Sie können ein Add-In für Office aus Visual Studio veröffentlichen. | [Bereitstellen und Veröffentlichen Ihres Office-Add-Ins](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF oder OData-Dienst** | Für andere Anwendungen können WCF RIA-Dienste verwendet werden, die Sie auf einem Webserver bereitstellen. | [Entwickeln und Bereitstellen von WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch wird ab Visual Studio 2017 nicht mehr unterstützt, kann aber aus Visual Studio 2015 und niedrigeren Versionen immer noch bereitgestellt werden. | [Bereitstellen von LightSwitch-Anwendungen](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie auf die Bereitstellungsoptionen für verschiedene Anwendungen einen kurzen Blick geworfen.

> [!div class="nextstepaction"]
> [Welche Optionen für die Veröffentlichung sind für mich geeignet?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
