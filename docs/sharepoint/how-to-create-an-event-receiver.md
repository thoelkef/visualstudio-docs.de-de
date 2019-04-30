---
title: 'Vorgehensweise: Erstellen eines Ereignisempfängers | Microsoft-Dokumentation'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc42a92e1d7dcc73bb6bc0433da4e6a31d7fefb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966756"
---
# <a name="how-to-create-an-event-receiver"></a>Vorgehensweise: Erstellen eines Ereignisempfängers
  Durch das Erstellen *Ereignisempfänger*, können Sie reagieren, wenn ein Benutzer mit SharePoint-Elemente wie Listen oder Listenelemente interagiert. Beispielsweise kann der Code in einem Ereignisempfänger ausgelöst werden, wenn ein Benutzer der Kalender geändert, oder einen Namen aus einer Liste "Kontakte löscht". Anhand der in diesem Thema erhalten Sie, wie Sie eine Listeninstanz eine Ereignisempfänger hinzufügen.

 Um diese Schritte abgeschlossen haben, müssen installiert sein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und die unterstützten Editionen von Windows und SharePoint. Da in diesem Beispiel wird ein SharePoint-Projekt erforderlich ist, Sie auch müssen abgeschlossen haben das Verfahren im Thema [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Hinzufügen eines Ereignisempfängers
 Das Projekt, das Sie in erstellt [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) enthält benutzerdefinierte Websitespalten, eine benutzerdefinierte Liste und einen Inhaltstyp. In der folgenden Prozedur müssen Sie dieses Projekt erweitern, durch Hinzufügen eines ereignishandlers für einfaches Ereignis (Ereignisempfänger) auf eine Listeninstanz zu zeigen, wie Sie Ereignisse behandeln, die in SharePoint-Elemente wie Listen auftreten.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Die Listeninstanz ein Ereignisempfänger hinzu

1. Öffnen Sie das Projekt, das Sie in erstellt [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. In **Projektmappen-Explorer**, wählen Sie die SharePoint-Projektknoten, mit dem Namen **Clinic**.

3. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

4. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.

5. In der **Vorlagen** Bereich wählen **Ereignisempfänger**, nennen Sie sie **"TestEventReceiver1" ein**, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

6. In der **welche Art von-Ereignisempfänger verwenden sollen?** wählen **Listenelementereignisse**.

7. In der **welche Artikel befinden sollte, die Ereignisquelle?** wählen **Patienten (Clinic\Patients)**.

8. In der **die folgenden Ereignisse behandeln** wählen Sie das Kontrollkästchen neben **ein Element wurde hinzugefügt**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     Die Codedatei für den neuen Ereignisempfänger enthält eine einzelne Methode mit dem Namen `ItemAdded`. Im nächsten Schritt wird: Fügen Sie Code für diese Methode, damit jeder wenden Sie sich an Scott Brown standardmäßig benannt ist.

9. Ersetzen Sie die vorhandene `ItemAdded` -Methode durch den folgenden code, und wählen Sie dann die **F5** Schlüssel:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Der Code ausgeführt wird, und die SharePoint-Website im Webbrowser wird angezeigt.

10. Wählen Sie auf der Schnellstartleiste der **Patienten** verknüpfen, und wählen Sie dann die **neues Element hinzufügen** Link.

     Der das Eintragsformular für neue Elemente geöffnet.

11. Geben Sie Daten in die Felder aus, und wählen Sie dann die **speichern** Schaltfläche.

     Nach Auswahl der **speichern** Schaltfläche der **Patient Name** Spalte, die automatisch auf den Namen Scott Brown aktualisiert werden.

## <a name="see-also"></a>Siehe auch

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)