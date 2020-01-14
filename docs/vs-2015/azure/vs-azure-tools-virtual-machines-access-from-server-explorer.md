---
title: Zugreifen auf virtuelle Azure-Computer über den Server-Explorer | Microsoft Docs
description: In diesem Artikel erhalten Sie einen Überblick darüber, wie virtuelle Azure-Computer im Server-Explorer von Visual Studio angezeigt, erstellt und verwaltet werden können.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: f4c1ff547d9d550cbbc2e77435b159543fc16bf6
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917099"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Zugreifen auf virtuelle Azure-Computer im Server-Explorer

Wenn Sie in Azure gehostete virtuelle Computer verwenden, können Sie über Server-Explorer auf diese Computer zugreifen. Sie müssen sich zunächst bei Ihrem Azure-Abonnement anmelden, um die mobilen Dienste anzeigen zu können. Öffnen Sie das Kontextmenü für den Azure-Knoten, und wählen Sie **Verbindung mit Microsoft Azure-Abonnement herstellen**aus, um sich anzumelden.

1. Wählen Sie im Cloud-Explorer einen virtuellen Computer aus, und drücken Sie anschließend die F4-Taste, um das Eigenschaftenfenster für den Computer anzuzeigen.

    Die folgende Tabelle zeigt, welche Eigenschaften verfügbar sind – diese jedoch alle schreibgeschützt. Sie können sie über das [Azure-Portal](https://portal.azure.com/) ändern.

   | Die Eigenschaften- | Beschreibung |
   | --- | --- |
   | DNS-Name |Die URL mit der Internetadresse des virtuellen Computers. |
   | -Umgebung |Für einen virtuellen Computer lautet der Wert dieser Eigenschaft immer "Produktion". |
   | -Name |Der Name des virtuellen Computers. |
   | -Größe |Die Größe des virtuellen Computers. Diese Eigenschaft gibt die Menge an verfügbarem Arbeitsspeicher und Festplattenspeicher an. Weitere Informationen finden Sie unter [Größen virtueller Computer](/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Mögliche Werte lauten "Wird gestartet", "Gestartet", "Wird angehalten", "Angehalten" und "Status wird abgerufen". Wird "Status wird abgerufen" angezeigt, ist der aktuelle Status unbekannt. Die Werte für diese Eigenschaft unterscheiden sich von den Werten, die im [Azure-Portal](https://portal.azure.com/) verwendet werden. |
   | SubscriptionID |Die Abonnement-ID für Ihr Azure-Konto. Sie können diese Informationen im [Azure-Portal](https://portal.azure.com/) anzeigen, indem Sie die Eigenschaften für ein Abonnement öffnen. |
2. Wählen Sie einen Endpunktknoten aus, und zeigen Sie dann das Fenster **Eigenschaften** an.
3. Die folgende Tabelle beschreibt die verfügbaren Endpunkteigenschaften. Alle Eigenschaften sind schreibgeschützt. Verwenden Sie zum Hinzufügen oder Bearbeiten der Endpunkte für einen virtuellen Computer das [Azure-Portal](https://portal.azure.com/). 

   | Die Eigenschaften- | Beschreibung |
   | --- | --- |
   | -Name |Ein Bezeichner für den Endpunkt. |
   | Privater Port |Der Port für den internen Netzwerkzugriff auf Ihre Anwendung. |
   | Protokoll |Das Protokoll, das von der Transportschicht für diesen Endpunkt verwendet wird – entweder TCP oder UDP. |
   | Öffentlicher Port |Der Port, der für den öffentlichen Zugang auf Ihrer Anwendung verwendet wird. |
