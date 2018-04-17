---
title: 'Vorgehensweise: Erstellen eines Ereignisempfängers | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: ead81e01022c8f389ad6010c89d0e433b82c542e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-event-receiver"></a>Gewusst wie: Erstellen eines Ereignisempfängers
  Durch das Erstellen *Ereignisempfänger*, können Sie reagieren, wenn ein Benutzer mit SharePoint-Elemente wie Listen oder Listenelemente interagiert. Beispielsweise kann der Code in einem Ereignisempfänger ausgelöst werden, wenn ein Benutzer den Kalender ändert oder einen Namen aus der Liste "Kontakte löscht". Anhand der in diesem Thema erfahren Sie, wie eine Listeninstanz einen Ereignisempfänger hinzugefügt werden.  
  
 Zum Ausführen dieser Schritte muss installiert sein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und die unterstützten Editionen von Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Da dieses Beispiel benötigen Sie ein SharePoint-Projekt, außerdem müssen Sie zunächst das Verfahren im Thema [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## <a name="adding-an-event-receiver"></a>Hinzufügen eines Ereignisempfängers  
 Das Projekt, das Sie erstellt haben [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) enthält benutzerdefinierte Websitespalten, einer benutzerdefinierten Liste und einen Inhaltstyp. Im folgenden Verfahren müssen Sie dieses Projekt erweitern, indem ein einfacher Ereignishandler (ein Ereignisempfänger) hinzufügen, eine Listeninstanz zu zeigen, wie Sie Ereignisse behandeln, die in SharePoint-Elemente wie Listen auftreten.  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Die Listeninstanz ein Ereignisempfänger hinzu  
  
1.  Öffnen Sie das Projekt, das Sie in erstellt [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  In **Projektmappen-Explorer**, wählen Sie den SharePoint-Projektknoten, mit dem Namen **Clinic**.  
  
3.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
4.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.  
  
5.  In der **Vorlagen** Bereich auswählen **Ereignisempfänger**, nennen Sie sie **"TestEventReceiver1" ein**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
6.  In der **Art-Ereignisempfänger verwenden, möchten Sie?** wählen **Listenelementereignisse**.  
  
7.  In der **welches Element der Ereignisquelle werden sollten?** wählen **Patienten (Clinic\Patients)**.  
  
8.  In der **die folgenden Ereignisse behandeln** wählen Sie das Kontrollkästchen neben **ein Element wurde hinzugefügt,**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Die Codedatei für die neue Ereignisempfänger enthält eine einzelne Methode mit dem Namen `ItemAdded`. Im nächsten Schritt müssen Sie dieser Methode Code hinzufügen, damit jeder wenden Sie sich an Standardeinstellung Scott Brown genannt werden soll.  
  
9. Ersetzen Sie die vorhandene `ItemAdded` -Methode durch folgenden code aus, und wählen Sie dann die F5-Taste:  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Der Code ausgeführt wird, und die SharePoint-Website im Webbrowser angezeigt wird.  
  
10. Wählen Sie in der Schnellstartleiste der **Patienten** verknüpfen, und wählen Sie dann die **neues Element hinzufügen** Link.  
  
     Das Eintragsformular für neue Elemente wird geöffnet.  
  
11. Geben Sie Daten in den Feldern, und wählen Sie dann die **speichern** Schaltfläche.  
  
     Nach dem Auswählen der **speichern** Schaltfläche, die **Patient Name** Spalte wird auf den Namen Scott Brown automatisch aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  