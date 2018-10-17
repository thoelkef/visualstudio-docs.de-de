---
title: 'Vorgehensweise: Herstellen einer Verbindung Daten in einem Dienst mit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce851a864dd11759c36c7ae6cb275e9e71cd11a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301794"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie verbinden Ihrer Anwendung für die Daten von einem Dienst zurückgegeben wird, mit der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , und wählen **Service** auf die **wählen Sie einen Datenquellentyp**Seite.  
  
 Nach Abschluss des Assistenten ein Dienstverweis wird dem Projekt hinzugefügt und ist sofort verfügbar ist, in der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Die Elemente in der **Datenquellen** hängen von den Informationen, die der Dienst zurückgibt. Einige Dienste möglicherweise nicht genug Informationen bieten die **Assistenten zur Datenquellenkonfiguration** bindbare Objekte erstellen. Z. B. wenn der Dienst ein nicht typisiertes Dataset zurückgibt, klicken Sie dann keine Elemente angezeigt werden der **Fensters "Datenquellen"** nach Abschluss des Assistenten. Das liegt nicht typisierte Datasets kein Schema angeben, damit der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Um Ihre Anwendung mit einem Dienst verbinden  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
2.  Wählen Sie **Service** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.  
  
3.  Geben Sie die Adresse des Diensts zu verwenden, oder klicken Sie auf **Discover** suchen Dienste in der aktuellen Projektmappe, und klicken Sie auf **wechseln**.  
  
4.  Optional ein neues **Namespace** anstelle der Standardwert eingegeben werden können.  
  
    > [!NOTE]
    >  Klicken Sie auf **erweitert** zum Öffnen der [Configure Service Reference Dialog Box](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Klicken Sie auf **OK** zum Hinzufügen eines Dienstverweises zum Projekt.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datenquelle wird hinzugefügt, um die **Datenquellen** Fenster.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
#### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Wählen Sie ein Element in der **Datenquellen** Fenster, und ziehen Sie es in ein Formular für das gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

