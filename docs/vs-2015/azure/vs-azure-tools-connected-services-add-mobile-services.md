---
title: Hinzufügen von Mobile Services mithilfe von verbundene Dienste
description: Hinzufügen von Mobile Services über das Visual Studio-Dialogfeld "Add verbundene Dienste"
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
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300190"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Hinzufügen von Mobile Services mithilfe von Visual Studio verbundene Dienste
Mit Visual Studio 2015 können Sie mithilfe des Dialog Felds **verbundenen Dienst hinzufügen** eine Verbindung mit Azure Mobile Services herstellen. Sie können eine Verbindung von C# jeder beliebigen Client-App, einer beliebigen JavaScript-APP oder einer plattformübergreifenden Cordova-App herstellen. Sobald Sie eine Verbindung hergestellt haben, können Sie Daten erstellen und darauf zugreifen, benutzerdefinierte APIs und geplante Aufträge erstellen oder Unterstützung für Pushbenachrichtigungen hinzufügen.  Der Vorgang "verbundene Dienste" fügt alle entsprechenden Verweise und den Verbindungs Code hinzu. Sie können auch die integrierte Unterstützung für die Authentifizierung mit einer Vielzahl beliebter Identitäts Schemas nutzen, wie z. b. Azure AD-, Facebook-, Twitter-und Microsoft-Konten.

## <a name="supported-project-types"></a>Unterstützte Projekttypen
> [!NOTE]
> In Visual Studio 2015 wird das Hinzufügen von Azure Mobile Services zu einem Windows Universal-Projekt (Windows 10) mithilfe des Dialog Felds "verbundene Dienste hinzufügen" nicht unterstützt. Sie können Azure-Mobile Services hinzufügen, indem Sie die entsprechenden Pakete mit dem nuget-Paket-Manager für Ihr Projekt installieren.
>
>

Sie können das Dialogfeld "verbundene Dienste" verwenden, um in den folgenden Projekttypen eine Verbindung mit Azure Mobile Services herzustellen.

* .NET Windows 8.1 Store-, Telefon-und universelle App-Projekte
* JavaScript-Windows 8.1 Store-, Telefon-und universelle App-Projekte
* Projekte, die mit Visual Studio-Tools für Apache Cordova erstellt wurden

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Herstellen einer Verbindung mit Azure Mobile Services mithilfe des Dialog Felds "verbundene Dienste hinzufügen
1. Stellen Sie sicher, dass Sie ein Azure-Konto besitzen. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://go.microsoft.com/fwlink/?LinkId=518146)registrieren.
2. Öffnen Sie das Dialogfeld **verbundene Dienste hinzufügen** .

   * Öffnen Sie für .net-apps das Projekt in Visual Studio, öffnen Sie das Kontextmenü für den Knoten **Verweise** in Projektmappen-Explorer, und wählen Sie dann **verbundenen Dienst hinzufügen** aus.

        ![Herstellen einer Verbindung mit Azure Mobile Service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Öffnen Sie für Apache Cordova App-Projekte das Projekt in Visual Studio, öffnen Sie das Kontextmenü für den Projekt Knoten in Projektmappen-Explorer, und wählen Sie dann **verbundenen Dienst hinzufügen**aus.
3. Wählen Sie im Dialogfeld **Verbundenen Dienst hinzufügen** **Azure Mobile Services** und wählen Sie dann die Schaltfläche **Konfigurieren**. Wenn Sie dies noch nicht getan haben, werden Sie möglicherweise aufgefordert, sich bei Azure anzumelden.

    ![Hinzufügen eines Azure Mobile Service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Wählen Sie im Dialogfeld des **Azure Mobile Services** einen vorhandenen mobilen Dienst, falls einer vorhanden ist. Wenn Sie einen neuen Azure Mobile Service erstellen müssen, befolgen Sie das unten beschriebene Verfahren. Andernfalls fahren Sie mit dem nächsten Schritt fort.

    So erstellen Sie ein neues mobiles Dienst Konto:

   1. Wählen Sie dafür den Link **Service erstellen** am unteren Rand des Dialogfelds.
       ![neuen mobilen verbundenen Dienst hinzufügen](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Im Dialogfeld **mobilen Dienst erstellen** können Sie in der Dropdown Liste **Runtime** einen mobilen JavaScript-Back-End-Dienst oder einen mobilen .net-Back-End-Dienst auswählen.

       ![Erstellen eines mobilen Dienstanbieter](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Ein JavaScript-Back-End-Dienst ist einfach und leistungsstark. Wenn Sie einen mobilen JavaScript-Back-End-Dienst erstellen, wird der serverseitige JavaScript-Code in der Cloud gespeichert. Sie können Serverskripts jedoch mit dem Server-Explorer oder dem bearbeiten Azure-Verwaltungsportal.

       Ein mobiler .net-Back-End-Dienst bietet Ihnen die volle Leistungsfähigkeit und Flexibilität von Web-API und Entity Framework. Wenn Sie einen mobilen .net-Back-End-Dienst erstellen, wird ein Projekt für Sie erstellt und der Projekt Mappe hinzugefügt.
   3. Wählen Sie die **Region**, in der Sie den mobilen Dienst nutzen möchten. Geben Sie dann einen Benutzernamen und ein Kennwort für den Server ein.
   4. Nachdem Sie alle erforderlichen Informationen eingegeben haben, wählen Sie **Erstellen**, um den mobilen Dienst zu erstellen.
   5. Der neue Mobile Dienst sollte im Dialogfeld **Azure Mobile Services** in der Liste Dienst angezeigt werden. Wählen Sie den neuen mobilen Dienst in der Liste aus und wählen Sie dann **Hinzufügen**, um den Dienst zu Ihrem Projekt hinzuzufügen.
5. Überprüfen Sie die Seite mit den ersten Schritten, die angezeigt wird, und erfahren Sie, wie das Projekt geändert wurde Die Seite Erste Schritte wird im Browser angezeigt, wenn Sie einen verbundenen Dienst hinzufügen. Sie können die empfohlenen ersten Schritte und Codebeispiele überprüfen oder zur Seite Was ist geschehen? wechseln, um herauszufinden, welche Verweise dem Projekt hinzugefügt wurden und wie Ihr Code und die Konfigurationsdateien geändert wurden.
6. Beginnen Sie mithilfe der Codebeispiele als Leitfaden mit dem Schreiben von Code für den Zugriff auf Ihren mobilen Dienst.

## <a name="how-your-project-is-modified"></a>Änderungen am Projekt
Wie Visual Studio das Projekt ändert, hängt vom Projekttyp ab. Informationen C# zu Client-apps finden Sie unter [Was ist passiert C# – Projekte](https://go.microsoft.com/fwlink/p/?LinkId=513119). Informationen zu JavaScript-Client-apps finden Sie unter [Was ist passiert – JavaScript-Projekte](https://go.microsoft.com/fwlink/p/?LinkId=513120). Informationen zu Cordova-apps finden Sie unter [Was ist passiert – Cordova-Projekte](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Nächste Schritte
Stellen Sie Fragen, und erhalten Sie Hilfe:

* [MSDN-Forum: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure-Mobile Services im Microsoft Azure Teamblog](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure-Mobile Services unter Azure.Microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Dokumentation zu Azure Mobile Services unter Azure.Microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
