---
title: 'Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0affe931e5b85d32acdc95fecaa50f3b7f2fe8f4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39175698"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Gewusst wie: Verbinden mit Daten in einem Dienst

Sie verbinden Ihrer Anwendung für die Daten von einem Dienst zurückgegeben wird, mit der [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png) , und wählen **Service** auf die **wählen Sie einen Datenquellentyp**Seite.

Nach Abschluss des Assistenten ein Dienstverweis wird dem Projekt hinzugefügt und ist sofort verfügbar ist, in der [Fensters "Datenquellen"](add-new-data-sources.md).

> [!NOTE]
> Die Elemente in der **Datenquellen** hängen von den Informationen, die der Dienst zurückgibt. Einige Dienste möglicherweise nicht genug Informationen bieten die **Assistenten zur Datenquellenkonfiguration** bindbare Objekte erstellen. Z. B. wenn der Dienst ein nicht typisiertes Dataset zurückgibt, keine Elemente angezeigt werden der **Fensters "Datenquellen"** nach Abschluss des Assistenten. Das liegt nicht typisierte Datasets kein Schema angeben, damit der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Um Ihre Anwendung mit einem Dienst verbinden

1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

2.  Wählen Sie **Service** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.

3.  Geben Sie die Adresse des Diensts zu verwenden, oder klicken Sie auf **Discover** suchen Dienste in der aktuellen Projektmappe, und klicken Sie auf **wechseln**.

4.  Optional können Sie ein neues eingeben **Namespace** anstelle des Standard-Werts.

    > [!NOTE]
    > Klicken Sie auf **erweitert** zum Öffnen der [Dialogfeld Dienstverweis konfigurieren](../data-tools/configure-service-reference-dialog-box.md).

5.  Klicken Sie auf **OK** zum Hinzufügen eines Dienstverweises zum Projekt.

6.  Klicken Sie auf **Fertig stellen**.

     Die Datenquelle wird hinzugefügt, um die **Datenquellen** Fenster.

## <a name="next-steps"></a>Nächste Schritte

Um Funktionen zu Ihrer Anwendung hinzuzufügen, wählen Sie ein Element in der **Datenquellen** Fenster, und ziehen Sie es in ein Formular für das gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Communication Foundation-Dienste und WCF-Datendienste in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)