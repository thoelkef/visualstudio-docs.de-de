---
title: Hinzufügen von Mobile Services mithilfe von verbundene Dienste
description: Hinzufügen von Mobile Services mithilfe der im Dialogfeld "Visual Studio verbundene Dienste hinzufügen"
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4bfda342952820b4472a1f826273a7b9075faa9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963972"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Hinzufügen von Mobile Services mithilfe von Visual Studio verbundene Dienste
Mit Visual Studio 2015, Sie können eine Verbindung herstellen mit Azure Mobile Services mithilfe der **verbundenen Dienst hinzufügen** Dialogfeld. Sie können von jedem verbinden C# Client-app, JavaScript-Apps oder plattformübergreifende Cordova-app. Nachdem Sie eine Verbindung herstellen, können Sie erstellen und auf Daten zugreifen, benutzerdefinierte APIs und geplante Aufträge erstellen oder Hinzufügen von Unterstützung für Pushbenachrichtigungen.  Der Vorgang für verbundene Dienste fügt alle entsprechenden Verweise und den Verbindungscode hinzu. Sie können auch nutzen, integrierte Unterstützung für die Authentifizierung mit einer Vielzahl von beliebten identitätsschemas wie Azure AD, Facebook, Twitter und Microsoft-Accounts.

## <a name="supported-project-types"></a>Unterstützte Projekttypen
> [!NOTE]
> In Visual Studio 2015 wird das Azure Mobile Services für eine universelle Windows (Windows 10) Projekte hinzugefügt, mit das Dialogfeld "verbundene Dienste hinzufügen" nicht unterstützt. Sie können Azure Mobile Services hinzufügen, indem Sie die entsprechenden Pakete mit den NuGet-Paket-Manager für Ihr Projekt installieren.
>
>

Sie können das Dialogfeld "verbundene Dienste" verwenden, in den folgenden Projekttypen eine Verbindung mit Azure Mobile Services.

* .NET Windows 8.1 Store, Phone und universelle App-Projekte
* JavaScript Windows 8.1 Store, Phone und universelle App-Projekte
* Erstellt mit Visual Studio-Tools für Apache Cordova-Projekten

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Verbinden Sie mit Azure Mobile Services verwenden das Dialogfeld "verbundene Dienste hinzufügen"
1. Stellen Sie sicher, dass Sie ein Azure-Konto verfügen. Wenn Sie nicht über ein Azure-Konto verfügen, registrieren Sie sich für eine [kostenlose Testversion](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Öffnen der **verbundene Dienste hinzufügen** Dialogfeld.

   * Bei .NET-Apps werden das Projekt in Visual Studio öffnen, öffnen Sie das Kontextmenü für die **Verweise** Knoten im Projektmappen-Explorer, und wählen Sie dann **verbundenen Dienst hinzufügen**

        ![Herstellen einer Verbindung mit Azure Mobile Services](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Öffnen Sie für Apache Cordova-app-Projekte, die Ihr Projekt in Visual Studio, öffnen Sie das Kontextmenü für den Projektknoten im Projektmappen-Explorer, und wählen Sie dann **verbundenen Dienst hinzufügen**.
3. In der **verbundenen Dienst hinzufügen** Dialogfeld wählen **Azure Mobile Services**, und wählen Sie dann die **konfigurieren** Schaltfläche. Sie werden möglicherweise aufgefordert, sich bei Azure anzumelden, wenn Sie dies nicht bereits getan haben.

    ![Hinzufügen eines mobilen Azure-Diensts](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. In der **Azure Mobile Services** Dialogfeld Feld, wählen Sie einen vorhandenen mobilen Dienst aus, falls vorhanden. Wenn Sie einen neuen mobilen Dienst erstellen möchten, gehen Sie zu diesem Zweck. Fahren Sie andernfalls mit dem nächsten Schritt.

    So erstellen Sie ein neues Konto für den mobilen Dienst:

   1. Wählen Sie die **Create Service** Link am unteren Rand des Dialogfelds.
       ![Hinzufügen eines neuen mobilen verbundenen Diensts](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Auf der **mobilen Service erstellen** im Dialogfeld können Sie einen mobilen JavaScript-Back-End-Dienst oder einen mobilen .NET Back-End-Dienst aus der **Runtime** Dropdown-Liste.

       ![Erstellen eines mobilen Diensts](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Ein JavaScript-Back-End-Dienst ist einfach und leistungsstark. Wenn Sie einen mobilen JavaScript-Back-End-Dienst erstellen, wird der serverseitige JavaScript-Code in der Cloud gespeichert, aber Sie können mithilfe von Server-Explorer oder das Azure-Verwaltungsportal Serverskripts bearbeiten.

       Ein mobiler .NET Back-End-Dienst bietet Ihnen die volle Leistungsfähigkeit und Flexibilität von Web-API und Entity Framework. Wenn Sie einen mobilen .NET Back-End-Dienst erstellen, wird ein Projekt für Sie erstellt und der Projektmappe hinzugefügt.
   3. Wählen Sie die **Region** , in dem Sie den mobilen Dienst, und klicken Sie dann einen Benutzernamen und ein Kennwort für den Server eingeben.
   4. Nachdem Sie alle erforderlichen Informationen eingegeben haben, wählen Sie die **erstellen** klicken, um den mobilen Dienst zu erstellen.
   5. Der neue mobile Dienst sollte angezeigt werden in der Liste der Dienste auf dem **Azure Mobile Services** Dialogfeld. Wählen Sie den neuen mobilen Dienst in der Liste aus, und wählen Sie dann die **hinzufügen** , um den Dienst zu Ihrem Projekt hinzuzufügen.
5. Überprüfen Sie die erste Seite "Schritte", der angezeigt wird, und erfahren Sie, wie Ihr Projekt geändert wurde. Eine Seite Erste Schritte, die in Ihrem Browser angezeigt werden, wenn Sie einen verbundenen Dienst hinzufügen. Sie können überprüfen, die vorgeschlagenen nächsten Schritte und Codebeispiele oder wechseln Sie zu der Seite "Was passiert ist", um herauszufinden, welche Verweise dem Projekt hinzugefügt wurden und wie Ihr Code und die Konfigurationsdateien geändert wurden.
6. Verwenden die Codebeispiele als Leitfaden, starten Sie das Schreiben von Code für den Zugriff auf Ihren mobilen Dienst!

## <a name="how-your-project-is-modified"></a>Änderungen am Projekt
Wie Visual Studio das Projekt ändert, hängt vom Projekttyp ab. Für C# -Client-apps finden Sie unter [Was ist passiert – C# Projekte](http://go.microsoft.com/fwlink/p/?LinkId=513119). JavaScript-Client-apps finden Sie unter [Was ist passiert – JavaScript-Projekte](http://go.microsoft.com/fwlink/p/?LinkId=513120). Cordova-apps finden Sie unter [Was ist passiert – Cordova Projekte](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Nächste Schritte
Stellen Sie Fragen und Hilfe:

* [MSDN-Forum: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services im Microsoft Azure-Teamblog](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure Mobile Services unter azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Azure Mobile Services-Dokumentation auf "Azure.Microsoft.com"](https://azure.microsoft.com/documentation/services/mobile-services/)
