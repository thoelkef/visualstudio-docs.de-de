---
title: Installieren und Verwenden von Visual Studio für Mac hinter einer Firewall oder einem Proxyserver
description: In diesem Dokument wird eine Liste der Hosts bereitgestellt, die von Ihrer Firewall zugelassen sein müssen, damit Visual Studio für Mac (und die zugehörigen Workloads, einschließlich Xamarin) in einer Unternehmensumgebung funktioniert.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 717eb9cd58f213c3d2c31a18c546a83ab8feb645
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984026"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installieren und Verwenden von Visual Studio für Mac hinter einer Firewall oder einem Proxyserver

Wenn Ihre Organisation Sicherheitsmechanismen wie eine Firewall oder einen Proxyserver verwendet, dann sollten Sie einige Domänen in die Zulassungsliste aufnehmen und verschiedene Ports und Protokolle öffnen bzw. deren Verwendung zulassen, um eine optimale Installation und Verwendung von Visual Studio für Mac und Azure-Diensten zu gewährleisten.

- [**Installieren von Visual Studio für Mac:** ](#install-visual-studio-for-mac) Diese Tabellen enthalten die Domänen, die Konnektivität zulassen müssen, damit Sie Zugriff auf alle Features und Workloads von Visual Studio für Mac haben.

- [**Verwenden von Visual Studio für Mac:** ](#use-visual-studio-for-mac) Diese Tabellen enthalten Domänen, die Konnektivität zulassen müssen, damit Sie Zugriff auf die entsprechenden Funktionen haben.

## <a name="install-visual-studio-for-mac"></a>Installieren von Visual Studio für Mac

Da der Visual Studio für Mac-Installer Dateien von verschiedenen Domänen und Downloadservern herunterlädt, finden Sie hier die Domänen und URLs, die Sie möglicherweise als vertrauenswürdig in Ihren Konfigurationen hinzufügen möchten.

### <a name="microsoft-domains"></a>Microsoft-Domänen

| Domäne| Zweck |
| ----------------------------------- |---------------------------|
| *.live.com| Verwalten von Anmeldeinformationen |
| app.vssps.visualstudio.com| Installer-Metadaten|
| vortex.data.microsoft.com | Absturz- und Fehlerberichterstattung |
| az667904.vo.msecnd.net| Absturz- und Fehlerberichterstattung |
| xamarin.com | Installer-Metadaten|
| xampubdl.blob.core.windows.net| Installer-Pakete|
| download.visualstudio.microsoft.com | Installer-Pakete|
| xamarin.azureedge.net | Installer-Pakete|
| developer.xamarin.com | Installer-Pakete|
| static.xamarin.com | Installer-Pakete|
| dl.xamarin.com | Installer-Pakete|
| dc.services.visualstudio.com| Absturzberichte |

### <a name="third-party-domains"></a>Drittanbieterdomänen

| Domäne| Zweck |
| --------------------------|-------------------------|
| dl.google.com | Android-SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple-Sicherheitsdienste |

## <a name="use-visual-studio-for-mac"></a>Verwenden Sie Visual Studio für Mac

Um sicherzustellen, dass Sie Zugriff auf alle Funktionen haben, die Sie in Visual Studio für Mac benötigen, während Sie sich hinter einem Proxy oder einer Firewall befinden, empfehlen wir, die folgenden Domänen und Ports in die Zulassungsliste für den Zugriff aufzunehmen.

### <a name="general"></a>Allgemein

| Domäne | Port(s)|Zweck|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft-URL-Auflösung |
| vsstartpage.blob.core.windows.net| 80/443| Daten für die Startseite|
| software.xamarin.com |  80/443|Updater-Dienst|
| addins.monodevelop.com | 80/443| Erweiterungsdienste |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Experimentelles Feature und Benachrichtigungen |
| targetednotifications.azurewebsites.net|  80/443| Dient zum Filtern einer globalen Liste mit Benachrichtigungen in eine Liste, die nur für bestimmte Computertypen/Verwendungsszenarien gilt.|

### <a name="identity"></a>Identität

| Domäne | Port(s)|Zweck|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Identitätsanbieter|
| secure.aadcdn.microsoftonline-p.com | 80/443|Identitätsanbieter|
| dc.services.visualstudio.com| 80/443|Absturzberichte|
| management.azure.com|80/443| Azure Services API |

### <a name="nuget"></a>NuGet

| Domäne | Port(s)|Zweck|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet-API|
| secure.aadcdn.microsoftonline-p.com |80/443| Identitätsanbieter|

### <a name="android-projects"></a>Android-Projekte

| Domäne| Zweck|
| ------------------------------------|------------------------------------|
| time.android.com| Zeitserver für Android-Emulator |
| connectivitycheck.gstatic.com | Konnektivität für Android-Emulator|
| cloudconfig.googleapis.com| APIs für Android-Emulator|

## <a name="see-also"></a>Siehe auch

- [Installieren und Verwenden von Visual Studio und Azure-Diensten hinter einer Firewall oder einem Proxyserver](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Problembehandlung ähnlicher Probleme unter Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
