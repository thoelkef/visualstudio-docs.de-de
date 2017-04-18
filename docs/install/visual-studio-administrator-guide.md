---
title: "Administratorhandbuch für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 04/03/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: fb7a87b720ad29252c602d9be5b958d8417ab93e
ms.lasthandoff: 04/03/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Administratorhandbuch für Visual Studio 2017

 Sie können Visual Studio in einem Netzwerk bereitstellen, solange jeder Zielcomputer die [minimalen Installationsanforderungen](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs) erfüllt.

 Egal, ob Sie über Software, z.B. System Center oder über eine Batchdatei bereitstellen, Sie sollten in der Regel die folgenden Schritte durchlaufen:

1. [Speichern Sie das Layout des Visual Studio-Produktlyouts](create-an-offline-installation-of-visual-studio.md) in einem Netzwerkordner zwischen.

2. [Wählen Sie die Arbeitsauslastungen und Komponenten](workload-and-component-ids.md) aus, die installiert werden sollen.

3. [Erstellen Sie ein Installationsskript](use-command-line-parameters-to-install-visual-studio.md) mithilfe der ausgewählten Elementen und anderen Befehlszeilenparametern zur Steuerung der Installation.

4. [Wenden Sie optional einen Volumenlizenz-Produktschlüssel](automatically-apply-product-keys-when-deploying-visual-studio.md) als Teil des Installationsskripts an, damit Benutzer die Software nicht separat aktivieren müssen.

5. Verwenden Sie zum Ausführen des Skripts auf der Ziel-Entwicklerarbeitsstationen die Bereitstellungstechnologie Ihrer Wahl.

6. Aktualisieren Sie den Netzwerkspeicherort mit den neuesten Updates zu Visual Studio durch Ausführen des Befehls, die Sie in Schritt 1 in regelmäßigen Abständen verwendet haben, um aktualisierte Komponenten hinzuzufügen.

> [!IMPORTANT]
>  Beachten Sie, dass sich Installationen über eine Netzwerkfreigabe den ursprünglichen Quellspeicherort „merken“. Dies bedeutet, dass Sie zur Reparatur eines Clients möglicherweise zur Netzwerkfreigabe zurückkehren müssen, über die der Client ursprünglich installiert wurde. Wählen Sie die Netzwerkadresse sorgfältig aus, sodass sie der Lebensdauer der Visual Studio 2017-Clients in Ihrer Organisation entspricht.

## <a name="tools"></a>Tools

 Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten können:

* [VSWhere](https://github.com/microsoft/vswhere): eine ausführbare C++-Datei, die Ihnen hilft, den Speicherort der wichtigsten Tools für Visual Studio in einer installierten Instanz von Visual Studio zu finden.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): PowerShell-Skripts, die die Setupkonfigurations-API zum Identifizieren der installierten Instanzen von Visual Studio verwenden.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): C#- und C++-Beispiele, die veranschaulichen, wie Sie die Setupkonfigurations-API zum Abfragen einer vorhandene Installation verwenden.

Darüber hinaus stellt die [Setupkonfigurations-API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) Schnittstellen für Entwickler bereit, die eigene Hilfsprogramme zum Abfragen von Visual Studio-Instanzen erstellen möchten.

>[!TIP]
>Weitere Informationen zur Installation von Visual Studio 2017 finden in den [Blogbeiträgen von Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Erstellen eines Offlineinstallationsprogramms für Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

