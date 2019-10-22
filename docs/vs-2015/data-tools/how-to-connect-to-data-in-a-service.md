---
title: 'Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654691"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie verbinden Ihre Anwendung mit den Daten, die von einem Dienst zurückgegeben werden, indem Sie den [Assistenten zum Konfigurieren von Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) ausführen und auf der Seite **Daten Quellentyp auswählen** die Option **Dienst** auswählen.

 Nach Abschluss des Assistenten wird dem Projekt ein Dienst Verweis hinzugefügt, der sofort im [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)verfügbar ist.

> [!NOTE]
> Die im Fenster **Datenquellen** angezeigten Elemente hängen von den vom Dienst zurückgegebenen Informationen ab. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Wenn der Dienst beispielsweise ein nicht typisiertes DataSet zurückgibt, werden beim Abschließen des Assistenten keine Elemente im **Datenquellen Fenster** angezeigt. Dies liegt daran, dass nicht typisierte Datasets kein Schema bereitstellen, sodass der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>So verbinden Sie Ihre Anwendung mit einem Dienst

1. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

2. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Dienst** aus, und klicken Sie dann auf **weiter**.

3. Geben Sie die Adresse des Diensts ein, den Sie verwenden möchten, oder klicken Sie auf **ermitteln** , um die Dienste in der aktuellen Projekt Mappe zu suchen, **und klicken Sie dann auf**

4. Optional kann ein neuer **Namespace** anstelle des Standardwerts eingegeben werden.

    > [!NOTE]
    > Klicken Sie auf **erweitert** , um das [Dialog Felddienst Verweis konfigurieren](../data-tools/configure-service-reference-dialog-box.md)zu öffnen.

5. Klicken Sie auf **OK** , um dem Projekt einen Dienst Verweis hinzuzufügen.

6. Klicken Sie auf **Fertig stellen**.

     Die Datenquelle wird dem Fenster **Datenquellen** hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

#### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu

- Wählen Sie im **Datenquellen** Fenster ein Element aus, und ziehen Sie es auf ein Formular, um gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
 [Binden von WPF-Steuerelementen an einen WCF Data Service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [-Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
