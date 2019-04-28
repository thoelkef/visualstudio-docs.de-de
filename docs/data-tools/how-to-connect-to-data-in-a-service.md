---
title: 'Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst'
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7633d60ed672b64137b68bd9e6c3b860224753e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566933"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst

Sie verbinden Ihrer Anwendung für die Daten von einem Dienst zurückgegeben wird, mit der [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png) , und wählen **Service** auf die **wählen Sie einen Datenquellentyp**Seite.

Nach Abschluss des Assistenten ein Dienstverweis wird dem Projekt hinzugefügt und ist sofort verfügbar ist, in der [Fenster "Datenquellen"](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Die im Fenster **Datenquellen** angezeigten Elemente hängen von den vom Dienst zurückgegebenen Informationen ab. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Z. B. wenn der Dienst ein nicht typisiertes Dataset zurückgibt, keine Elemente angezeigt werden der **Datenquellen** Fenster nach Abschluss des Assistenten. Das liegt nicht typisierte Datasets kein Schema angeben, damit der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Um Ihre Anwendung mit einem Dienst verbinden

1. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

2. Wählen Sie **Service** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.

3. Geben Sie die Adresse des Diensts zu verwenden, oder klicken Sie auf **Discover** suchen Dienste in der aktuellen Projektmappe, und klicken Sie auf **wechseln**.

4. Optional können Sie ein neues eingeben **Namespace** anstelle des Standard-Werts.

    > [!NOTE]
    > Klicken Sie auf **erweitert** zum Öffnen der [Dialogfeld Dienstverweis konfigurieren](../data-tools/configure-service-reference-dialog-box.md).

5. Klicken Sie auf **OK** zum Hinzufügen eines Dienstverweises zum Projekt.

6. Klicken Sie auf **Fertig stellen**.

     Die Datenquelle wird dem Fenster **Datenquellen** hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

Um Funktionen zu Ihrer Anwendung hinzuzufügen, wählen Sie ein Element in der **Datenquellen** Fenster, und ziehen Sie es in ein Formular für das gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)