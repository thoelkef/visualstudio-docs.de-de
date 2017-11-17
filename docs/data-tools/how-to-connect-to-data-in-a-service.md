---
title: 'Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 334f31dcd68e031bfb25b4e0dcd6ce55b9d2f20c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-connect-to-data-in-a-service"></a>Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst
Verbinden Sie die Anwendung die Daten, die durch das Ausführen von einem Dienst zurückgegeben der [Datenquellen Konfigurations-Assistenten](../data-tools/media/data-source-configuration-wizard.png) auswählen und **Service** auf die **wählen Sie einen Datenquellentyp**Seite.  
  
 Nach Abschluss des Assistenten wird ein Dienstverweis wird dem Projekt hinzugefügt und ist sofort verfügbar ist, in der [Datenquellenfenster](add-new-data-sources.md).  
  
> [!NOTE]
>  Die Elemente in der **Datenquellen** hängen von den der Dienst zurückgegebenen Informationen ab. Einige Dienste möglicherweise nicht genügend Informationen bereit, die **Data Source Configuration Wizard** bindbare Objekte erstellen. Beispielsweise, wenn der Dienst ein nicht typisiertes Dataset zurückgibt, dann keine Elemente angezeigt werden der **Datenquellenfenster** nach Abschluss des Assistenten. Dies ist, da nicht typisierte Datasets kein Schema angeben, damit der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Um Ihre Anwendung mit einem Dienst verbinden  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
2.  Wählen Sie **Service** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.  
  
3.  Geben Sie die Adresse des Diensts zu verwenden, oder klicken Sie auf **Discover** suchen Dienste in der aktuellen Projektmappe, und klicken Sie dann auf **Go**.  
  
4.  Optional ein neues **Namespace** anstelle der Standardwert eingegeben werden können.  
  
    > [!NOTE]
    >  Klicken Sie auf **erweitert** So öffnen die [konfigurieren Dienst Dialogfelds "Verweis"](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Klicken Sie auf **OK** zum Hinzufügen eines Dienstverweises zum Projekt.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datenquelle hinzugefügt wird die **Datenquellen** Fenster.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
#### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Wählen Sie ein Element in der **Datenquellen** Fenster, und ziehen sie ein Formular für gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)