---
title: Zugreifen auf virtuelle Azure-Computer im Server-Explorer | Microsoft-Dokumentation
description: Verschaffen Sie sich ein Überblick über die anzeigen, erstellen und Verwalten von virtuellen Azure-Computern (VMs) im Server-Explorer in Visual Studio.
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001710"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Zugreifen auf virtuelle Azure-Computer im Server-Explorer

Wenn Sie von Azure gehosteten virtuellen Computer verfügen, können Sie sie im Server-Explorer zugreifen. Sie müssen zuerst auf Ihrem Azure-Abonnement anmelden, die mobilen Dienste anzeigen. Um sich anzumelden, öffnen Sie das Kontextmenü für den Azure-Knoten im Server-Explorer, und wählen **Herstellen einer Verbindung mit Microsoft Azure**.

1. Wählen Sie einen virtuellen Computer im Cloud-Explorer, und wählen Sie dann die F4-Taste, um das Eigenschaftenfenster anzuzeigen.

    Die folgende Tabelle zeigt, welche Eigenschaften verfügbar sind, aber sie sind alle schreibgeschützt. Um diese zu ändern, verwenden die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Eigenschaft | Beschreibung |
   | --- | --- |
   | DNS-Name |Die URL mit der Internetadresse des virtuellen Computers. |
   | Umgebung |Für einen virtuellen Computer lautet der Wert dieser Eigenschaft immer Produktion. |
   | name |Der Name des virtuellen Computers. |
   | Größe |Die Größe des virtuellen Computers, die die Menge an Arbeitsspeicher und Speicherplatz angibt, die verfügbar ist. Weitere Informationen finden Sie unter [VM-Größen](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Werte sind gestartet, gestartet, beendet, beendet und der Status abgerufen werden. Wenn das Abrufen von Status angezeigt wird, ist der aktuelle Status unbekannt. Die Werte für diese Eigenschaft unterscheiden sich von der Werte, mit denen auf die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | Abonnement-ID |Die Abonnement-ID für Ihr Azure-Konto. Sie können diese Informationen anzeigen, auf die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) durch Anzeigen der Eigenschaften für ein Abonnement. |
2. Wählen Sie einen Endpunktknoten aus, und zeigen Sie dann die **Eigenschaften** Fenster.
3. Die folgende Tabelle beschreibt die verfügbaren Eigenschaften von Endpunkten, aber sie sind schreibgeschützt. Verwenden Sie zum Hinzufügen oder Bearbeiten der Endpunkte für einen virtuellen Computer, die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Eigenschaft | Beschreibung |
   | --- | --- |
   | name |Ein Bezeichner für den Endpunkt. |
   | Privater Port |Der Port für den internen Netzwerkzugriff auf Ihre Anwendung. |
   | Protokoll |Das Protokoll, das die Transportschicht für diesen Endpunkt verwendet wird, entweder TCP oder UDP. |
   | Öffentlicher Port |Der Port, der für den öffentlichen Zugriff für Ihre Anwendung verwendet wird. |
