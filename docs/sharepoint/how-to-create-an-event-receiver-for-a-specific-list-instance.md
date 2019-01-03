---
title: 'Vorgehensweise: Erstellen eines Ereignisempfängers für eine bestimmte Listeninstanz | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a92b86d7e02487ff333fb8517086f9c6221d35ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818861"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Vorgehensweise: Erstellen eines Ereignisempfängers für eine bestimmte Listeninstanz
  Ein Ereignisempfänger für Liste Instanz reagiert auf Ereignisse, die in einer beliebigen Instanz von einer Listendefinition auftreten. Auch wenn die ereignisvorlage für den Empfänger nicht die Zielgruppenadressierung von eine bestimmte Listeninstanz aktiviert wird, können Sie einen Ereignisempfänger ändern, der auf einer Listendefinition Reaktion auf Ereignisse in eine bestimmte Listeninstanz begrenzt ist.  
  
 Eine bestimmte Listeninstanz im Ziel die *"Elements.xml"* ersetzen Sie für einen Ereignisempfänger `ListTemplateId` mit `ListUrl` und die URL der Listeninstanz hinzufügen.  
  
## <a name="create-a-list-instance-event-receiver"></a>Erstellen Sie einen Liste Instanz-Ereignisempfänger  
 Die folgenden Schritte zeigen, wie einen Ereignisempfänger für Liste Element nur auf Ereignisse reagiert werden soll, die auftreten, in einer Instanz des benutzerdefinierten Ankündigungen-Liste geändert wird.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>So ändern Sie einen Ereignisempfänger zum Reagieren auf eine bestimmte Listeninstanz  
  
1.  Öffnen Sie in einem Browser die SharePoint-Website.  
  
2.  Klicken Sie im Navigationsbereich **listet** Link.  
  
3.  In der **Alle Websiteinhalte einblenden** Seite die **erstellen** Link.  
  
4.  In der **erstellen** Dialogfeld auf die **Ankündigungen** geben, benennen Sie die Ankündigung **TestAnnouncements**, und wählen Sie dann die **erstellen**Schaltfläche.  
  
5.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ein Ereignisempfängerprojekt erstellen.  
  
6.  In der **welche Art von-Ereignisempfänger verwenden sollen?** wählen **Listenelementereignisse**.  
  
    > [!NOTE]  
    >  Sie können auch eine andere Art von Ereignisempfänger, die für die Listendefinition einer, z. B. Bereiche auswählen **Listen-e-Mail-Ereignisse** oder **Listenworkflowereignisse**.  
  
7.  In der **welche Artikel befinden sollte, die Ereignisquelle?** wählen **Ankündigungen**.  
  
8.  In der **die folgenden Ereignisse behandeln** Liste der **ein Element hinzugefügt wird** aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
9. In **Projektmappen-Explorer**, öffnen Sie unter EventReceiver1, *"Elements.xml"*.  
  
     Ereignisempfänger verweist derzeit die Listendefinition Ankündigungen mithilfe der folgenden Zeile:  
  
    ```xml  
    <Receivers ListTemplateId="104">  
    ```  
  
     Ändern Sie diese Zeile, die folgendem Text:  
  
    ```xml  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Dies weist den Ereignisempfänger, um nur auf Ereignisse zu reagieren, die auftreten, in der neuen **TestAnnouncements** Ankündigungsliste, die Sie gerade erstellt haben. Sie können ändern, die `ListURL` Attribut auf eine beliebige Listeninstanz auf dem SharePoint-Server verweisen.  
  
10. Öffnen Sie die Codedatei für den Ereignisempfänger, und fügen Sie einen Haltepunkt in der ItemAdding-Methode.  
  
11. Wählen Sie die **F5** -Taste, um die Projektmappe erstellen und ausführen.  
  
12. Wählen Sie in SharePoint, die **TestAnnouncements** Link im Navigationsbereich.  
  
13. Wählen Sie die **neue Ankündigung hinzufügen** Link.  
  
14. Geben Sie einen Titel für die Ankündigung, und wählen Sie dann die **speichern** Schaltfläche.  
  
     Beachten Sie, dass der Haltepunkt erreicht wird, wenn die Ankündigungsliste der benutzerdefinierten das neue Element hinzugefügt wird.  
  
15. Wählen Sie die **F5** Taste, um fortzusetzen.  
  
16. Wählen Sie im Navigationsbereich die **listet** verknüpfen, und wählen Sie dann die **Ankündigungen** Link.  
  
17. Fügen Sie eine neue Ankündigung an.  
  
     Beachten Sie, die der Ereignisempfänger nicht auf die neue Ankündigung ausgelöst wird, da der Empfänger konfiguriert ist, um nur auf Ereignisse in der Liste benutzerdefinierten ankündigungslistenerdienst zu reagieren **TestAnnouncements**.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)  
