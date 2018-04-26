---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud mit Visual Studio, Schritt 4: Debuggen eines Containers in Kubernetes | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Erste Schritte in Connected Environment mit .NET Core und Visual Studio

Vorheriger Schritt: [Erstellen einer Entwicklungsumgebung in Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Debuggen eines Containers in Kubernetes
Sobald die Entwicklungsumgebung erfolgreich erstellt wurde, können Sie die Anwendung debuggen. Legen Sie einen Breakpoint im Code fest, z.B. Zeile 20 in der Datei `HomeController.cs`, in der die Variable `Message` festgelegt ist. Drücken Sie die Taste **F5**, um mit dem Debuggen zu beginnen. 

Visual Studio kommuniziert mit der Entwicklungsumgebung, um die Anwendung zu erstellen und bereitzustellen und öffnet dann einen Browser, auf dem die Web-App ausgeführt wird. Möglicherweise sieht es so aus, als werde der Container lokal ausgeführt, obwohl er eigentlich in der Entwicklungsumgebung in Azure ausgeführt wird. Die Localhost-Adresse wird angegeben, da Connected Environment einen temporären SSH-Tunnel zum Container erstellt, der in Azure ausgeführt wird.

Klicken Sie oben auf der Seite auf den **Info**-Link, um den Breakpoint auszulösen. Genau wie bei lokal ausgeführtem Code verfügen Sie über Vollzugriff auf die Debuginformationen, z.B. die Aufrufliste, lokale Variablen, Ausnahmeinformationen usw.

> [!div class="nextstepaction"]
> [Aufrufen eines weiteren Containers](get-started-netcore-visualstudio-05.md)