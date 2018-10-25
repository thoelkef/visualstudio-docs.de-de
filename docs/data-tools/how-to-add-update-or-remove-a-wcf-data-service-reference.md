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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9099c1ee0b1ed3af108c11792f7629453dfbf7c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819042"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Gewusst wie: hinzufügen, aktualisieren oder entfernen ein WCF-Datendienstverweises
Ein *Dienstverweis* ermöglicht einem Projekt für den Zugriff auf eine oder mehrere [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Verwenden der **Hinzufügen eines Dienstverweises** Dialogfeld zu suchende [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in der aktuellen Projektmappe lokal auf einem lokalen Netzwerk oder im Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Hinzufügen eines Dienstverweises

### <a name="to-add-a-reference-to-an-external-service"></a>Einen Verweis auf einen externen Dienst hinzufügen

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens für das Projekt, Sie fügen Sie den Dienst, und klicken Sie dann auf **Hinzufügen eines Dienstverweises**.

     Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

2.  In der **Adresse** , geben Sie die URL für den Dienst, und klicken Sie dann auf **wechseln** für den Dienst zu suchen. Wenn der Dienst benutzersicherheit und das Kennwort implementiert, werden Sie möglicherweise für einen Benutzernamen und Kennwort aufgefordert.

    > [!NOTE]
    >  Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen. Wenn Sie Verweise aus nicht vertrauenswürdigen Quellen hinzufügen, hat das möglicherweise Auswirkungen auf die Sicherheit.

     Sie können auch auswählen, die URL aus der **Adresse** Liste, die vorherigen 15 URLs gespeichert, an dem gültigen Dienstmetadaten gefunden.

     Eine Statusanzeige eingeblendet, wenn die Suche durchgeführt wird. Sie können die Suche zu einem beliebigen Zeitpunkt beenden, indem Sie auf **beenden**.

3.  In der **Services** aus, erweitern Sie den Knoten für den Dienst, den Sie verwenden möchten und wählen Sie eine Entitätenmenge.

4.  In der **Namespace** Geben Sie den Namespace, der für den Verweis verwendet werden sollen.

5.  Klicken Sie auf **OK** um den Verweis dem Projekt hinzuzufügen.

     Ein Dienstclient (Proxy) wird generiert, und Metadaten, die den Dienst beschreibt hinzugefügt wird die *"App.config"* Datei.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Um einen Verweis auf einen Dienst in der aktuellen Projektmappe hinzuzufügen.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens für das Projekt, Sie fügen Sie den Dienst, und klicken Sie dann auf **Hinzufügen eines Dienstverweises**.

    Die **Hinzufügen eines Dienstverweises** Dialogfeld wird angezeigt.

2. Klicken Sie auf **ermitteln**.

    Alle Dienste (sowohl [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] und WCF-Dienste) in der aktuellen Projektmappe hinzugefügt werden die **Services** Liste.

3. In der **Services** aus, erweitern Sie den Knoten für den Dienst, den Sie verwenden möchten und wählen Sie eine Entitätenmenge.

4. In der **Namespace** Geben Sie den Namespace, der für den Verweis verwendet werden sollen.

5. Klicken Sie auf **OK** um den Verweis dem Projekt hinzuzufügen.

    Ein Dienstclient (Proxy) generiert und Metadaten, die den Dienst beschreibt hinzugefügt wird die *"App.config"* Datei.

## <a name="update-a-service-reference"></a>Aktualisieren eines Dienstverweises
 Das Entity Data Model für eine [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] manchmal ändert. In diesem Fall müssen Sie den Dienstverweis aktualisieren.

### <a name="to-update-a-service-reference"></a>Um einen Dienstverweis aktualisieren

-   In **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **Dienstverweis aktualisieren**.

     Ein Statusdialogfeld wird angezeigt, während der Verweis wird von ihrem ursprünglichen Speicherort aktualisiert, und der Dienstclient erneut generiert wird, um die Änderungen in den Metadaten widergespiegelt werden.

## <a name="remove-a-service-reference"></a>Entfernen eines Dienstverweises
 Wenn Sie ein Dienstverweis nicht mehr verwendet wird, können Sie es aus der Projektmappe entfernen.

### <a name="to-remove-a-service-reference"></a>So entfernen Sie einen Dienstverweis

-   In **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **löschen**.

     Client des Diensts aus der Projektmappe entfernt werden, und Metadaten, die den Dienst zu beschreiben, entfernt werden, aus der *"App.config"* Datei.

    > [!NOTE]
    >  Code, der den Dienstverweis verweist, muss manuell entfernt werden.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF-Datendienste in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)