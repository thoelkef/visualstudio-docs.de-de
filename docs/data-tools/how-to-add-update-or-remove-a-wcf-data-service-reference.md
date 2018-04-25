---
title: 'Gewusst wie: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4dba04455c4ac6ea6d124911b836d24ab2ec63ec
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Gewusst wie: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises
Ein *Dienstverweis* kann ein Projekt für den Zugriff auf eine oder mehrere [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Verwenden der **Hinzufügen eines Dienstverweises** Dialogfeld zu suchende [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in der aktuellen Projektmappe, lokal auf einem lokalen Netzwerk oder im Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-a-service-reference"></a>Hinzufügen eines Dienstverweises

#### <a name="to-add-a-reference-to-an-external-service"></a>So fügen Sie einen Verweis auf einen externen Dienst hinzu

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens des Projekts, das Sie verwenden möchten, fügen den Dienst, und klicken Sie dann auf **Hinzufügen eines Dienstverweises**.

     Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

2.  In der **Adresse** Feld Geben Sie die URL für den Dienst, und klicken Sie dann auf **Go** , für den Dienst gesucht werden soll. Wenn der Dienst-Namen und das Kennwort benutzersicherheit implementiert, können Sie für einen Benutzernamen und Kennwort aufgefordert.

    > [!NOTE]
    >  Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen. Wenn Sie Verweise aus nicht vertrauenswürdigen Quellen hinzufügen, hat das möglicherweise Auswirkungen auf die Sicherheit.

     Sie können auch auswählen, die URL aus der **Adresse** Liste aus, die der vorhergehenden 15 URLs speichert, an dem gültigen Dienstmetadaten gefunden wurde.

     Eine Statusanzeige wird angezeigt, wenn die Suche durchgeführt wird. Sie können die Suche jederzeit beenden, indem Sie auf **beenden**.

3.  In der **Services** aus, erweitern Sie den Knoten für den Dienst, den Sie verwenden möchten und wählen Sie eine Entitätenmenge.

4.  In der **Namespace** Geben Sie den Namespace, der für den Verweis verwendet werden sollen.

5.  Klicken Sie auf **OK** der Verweis auf das Projekt hinzufügen.

     Ein Dienstclient (Proxy) wird generiert, und Metadaten, die den Dienst beschreibt die Datei "App.config" hinzugefügt wird.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>So fügen Sie einen Verweis auf einen Dienst in der aktuellen Projektmappe hinzu

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens des Projekts, das Sie verwenden möchten, fügen den Dienst, und klicken Sie dann auf **Hinzufügen eines Dienstverweises**.

     Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

2.  Klicken Sie auf **ermitteln**.

     Alle Dienste (sowohl [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] und WCF-Dienste) in der aktuellen Projektmappe hinzugefügt werden die **Services** Liste.

3.  In der **Services** aus, erweitern Sie den Knoten für den Dienst, den Sie verwenden möchten und wählen Sie eine Entitätenmenge.

4.  In der **Namespace** Geben Sie den Namespace, der für den Verweis verwendet werden sollen.

5.  Klicken Sie auf **OK** der Verweis auf das Projekt hinzufügen.

     Ein Dienstclient (Proxy) wird generiert, und Metadaten, die den Dienst beschreibt die Datei "App.config" hinzugefügt wird.

## <a name="updating-a-service-reference"></a>Aktualisieren eines Dienstverweises
 Das Entity Data Model für eine [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] wird in einigen Fällen ändern. In diesem Fall muss der Dienstverweis aktualisiert werden.

#### <a name="to-update-a-service-reference"></a>Beim Aktualisieren eines Dienstverweises

-   In **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **Update Dienstverweis**.

     Während der Verweis vom ursprünglichen Speicherort aktualisiert wird, und der Dienstclient erneut generiert, um die Änderungen in den Metadaten widergespiegelt werden, wird ein Fortschrittsdialogfeld angezeigt.

## <a name="removing-a-service-reference"></a>Entfernen eines Dienstverweises
 Wenn Sie ein Dienstverweis nicht mehr verwendet wird, können Sie es aus der Projektmappe entfernen.

#### <a name="to-remove-a-service-reference"></a>Entfernen ein Dienstverweises

-   In **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **löschen**.

     Der Dienstclient wird aus der Projektmappe entfernt, und Metadaten, die den Dienst zu beschreiben, aus der Datei "App.config" entfernt werden.

    > [!NOTE]
    >  Jeglicher Code, der den Dienstverweis verweist, müssen manuell entfernt werden.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)