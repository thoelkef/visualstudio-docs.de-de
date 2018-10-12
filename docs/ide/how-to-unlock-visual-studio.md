---
title: 'Vorgehensweise: Entsperren von Visual Studio'
ms.date: 07/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c3f6bed7cc010f0aeaff22cd46eb7bcaaa4caf6
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280622"
---
# <a name="how-to-unlock-visual-studio"></a>Vorgehensweise: Entsperren von Visual Studio

Sie können Visual Studio bis zu 30 Tage lang kostenlos testen. Durch Anmelden bei der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) verlängert sich der Testzeitraum auf 90 Tage. Um Visual Studio weiterhin zu verwenden, entsperren Sie die IDE-Schnittstelle, indem Sie

- ein Onlineabonnement verwenden oder

- einen Product Key eingeben.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>So entsperren Sie Visual Studio mithilfe eines Onlineabonnements

Gehen Sie folgendermaßen vor, um Visual Studio mithilfe eines Visual Studio-Abonnements oder einer Azure DevOps Services-Organisation zu entsperren, der ein Microsoft-Konto oder ein Geschäfts-, Schul- oder Unikonto zugeordnet ist:

1. Klicken Sie auf die Schaltfläche **Anmelden** in der rechten oberen Ecke der IDE (oder wechseln Sie zu **Datei** >  **Kontoeinstellungen**, um das Dialogfeld **Kontoeinstellungen** zu öffnen, und klicken Sie auf die Schaltfläche **Anmelden**).

1. Geben Sie die Anmeldeinformationen für ein Microsoft-Konto oder ein Geschäfts- bzw. Schulkonto ein. Visual Studio sucht daraufhin nach einem Visual Studio-Abonnement oder einer Azure DevOps Services-Organisation, die Ihrem Konto zugeordnet ist.

> [!IMPORTANT]
> Visual Studio sucht automatisch nach mit dem Konto verknüpften Onlineabonnements, wenn Sie eine Verbindung mit einer Azure DevOps Services-Organisation im **Team Explorer**-Toolfenster herstellen. Wenn Sie eine Verbindung mit einer Azure DevOps Services-Organisation herstellen, können Sie sich sowohl mithilfe von Microsoft- als auch mit Geschäfts-, Schul- oder Unikonten anmelden. Wenn ein Onlineabonnement für dieses Benutzerkonto vorhanden ist, wird die IDE-Schnittstelle automatisch durch Visual Studio für Sie entsperrt.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>So entsperren Sie Visual Studio mit einem Product Key

1. Klicken Sie auf **Datei** > **Kontoeinstellungen**, um das Dialogfeld **Kontoeinstellungen** zu öffnen, und klicken Sie auf den Link **Mit einem Product Key lizenzieren**.

Geben Sie den Product Key an der dafür vorgesehenen Stelle ein.

> [!TIP]
> Vorabversionen von Visual Studio verfügen über keine Product Keys. Sie müssen sich bei der IDE-Schnittstelle anmelden, um Vorabversionen zu verwenden.

## <a name="address-license-problem-states"></a>Beheben von Lizenzproblemen

### <a name="update-stale-licenses"></a>Aktualisieren veralteter Lizenzen

 Sie kennen vermutlich die Visual Studio-Meldung zu einer abgelaufenen Lizenz: „Ihre Lizenz ist abgelaufen und muss aktualisiert werden.“

 ![Visual Studio-Meldung zu abgelaufener Lizenz](../ide/media/vs2017_stale-license.png)

 Diese Meldung gibt an, dass Ihr Abonnement zwar ggf. noch immer gültig ist, das von Visual Studio für Ihr Abonnement verwendete Lizenztoken jedoch nicht aktualisiert wurde und aus einem der folgenden Gründe abgelaufen ist:

- Sie haben Visual Studio nicht verwendet oder hatten über einen längeren Zeitraum keine Internetzugang.
- Sie haben sich bei Visual Studio abgemeldet.

Bevor das Lizenztoken abläuft, zeigt Visual Studio eine Warnmeldung an, in der Sie aufgefordert werden, Ihre Anmeldeinformationen erneut einzugeben.

Wenn Sie Ihre Anmeldeinformationen nicht erneut eingeben, beginnt der Ablaufzeitraum für das Token, und im Dialogfeld **Kontoeinstellungen** wird angezeigt, wie viele Tage noch verbleiben, bevor das Token vollständig abläuft. Nachdem das Token abgelaufen ist, müssen Sie Ihre Anmeldeinformationen für dieses Konto oder diese Lizenz mithilfe einer anderen der oben genannten Methoden erneut eingeben, bevor Sie Visual Studio weiterhin verwenden können.

> [!Important]
> Bei Verwendung von Visual Studio für einen längeren Zeitraum in Umgebungen mit wenig oder keinem Internetzugang sollten Sie einen Product Key verwenden, um Visual Studio zu entsperren, um Unterbrechungen zu vermeiden.

### <a name="update-expired-licenses"></a>Aktualisieren abgelaufener Lizenzen

 Wenn Ihr Abonnement vollständig abgelaufen ist und Sie keine Zugriffsrechte mehr für Visual Studio besitzen, müssen Sie Ihr Abonnement erneuern oder ein anderes Konto hinzufügen, das über ein Abonnement verfügt. Wechseln Sie zu **Datei** > **Kontoeinstellungen**, um weitere Informationen über die verwendete Lizenz zu erhalten. Die Lizenzinformationen werden auf der rechten Seite des Dialogfelds angezeigt. Wenn Sie über ein weiteres Abonnement verfügen, das mit einem anderen Konto verknüpft ist, fügen Sie dieses Konto zur Liste **Alle Konten** auf der linken Seite des Dialogfelds hinzu, indem Sie auf den Link **Konto hinzufügen** klicken.

## <a name="see-also"></a>Siehe auch

* [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md)