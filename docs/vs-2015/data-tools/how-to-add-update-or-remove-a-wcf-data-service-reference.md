---
title: 'Vorgehensweise: Hinzufügen, aktualisieren oder Entfernen eines WCF-Datendienst Verweises | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670006"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Gewusst wie: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *Dienst Verweis* ermöglicht einem Projekt den Zugriff auf eine oder mehrere [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] . Verwenden Sie das Dialogfeld **Dienstverweis hinzufügen** , um [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in der aktuellen Projekt Mappe lokal, in einem lokalen Netzwerk oder im Internet zu suchen.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Hinzufügen eines Dienst Verweises

#### <a name="to-add-a-reference-to-an-external-service"></a>So fügen Sie einen Verweis auf einen externen Dienst hinzu

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Namen des Projekts, dem Sie den Dienst hinzufügen möchten, und klicken Sie dann auf **Dienstverweis hinzufügen**.

     Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.

2. Geben Sie im Feld **Adresse** die URL für den Dienst ein, und klicken Sie dann auf **suchen, um** nach dem Dienst zu suchen. Wenn der Dienst Benutzernamen-und Kenn Wort Sicherheit implementiert, werden Sie möglicherweise aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

    > [!NOTE]
    > Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen. Wenn Sie Verweise aus nicht vertrauenswürdigen Quellen hinzufügen, hat das möglicherweise Auswirkungen auf die Sicherheit.

     Sie können auch die URL aus der **Adress** Liste auswählen, in der die vorherigen 15 URLs gespeichert sind, bei denen gültige Dienst Metadaten gefunden wurden.

     Eine Statusanzeige wird angezeigt, wenn die Suche ausgeführt wird. Sie können die Suche jederzeit abbrechen, indem Sie auf " **Abbrechen**" klicken.

3. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

4. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

5. Klicken Sie auf **OK**, um dem Projekt den Verweis hinzuzufügen.

     Es wird ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der app.config Datei hinzugefügt.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>So fügen Sie einen Verweis auf einen Dienst in der aktuellen Projekt Mappe hinzu

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Namen des Projekts, dem Sie den Dienst hinzufügen möchten, und klicken Sie dann auf **Dienstverweis hinzufügen**.

     Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.

2. Klicken Sie auf **ermitteln**.

     Alle Dienste (sowohl [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] als auch WCF-Dienste) in der aktuellen Projekt Mappe werden der Liste der **Dienste** hinzugefügt.

3. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

4. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

5. Klicken Sie auf **OK**, um dem Projekt den Verweis hinzuzufügen.

     Es wird ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der app.config Datei hinzugefügt.

## <a name="updating-a-service-reference"></a>Aktualisieren eines Dienst Verweises
 Die Entity Data Model für eine [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] wird manchmal geändert. In diesem Fall muss der Dienst Verweis aktualisiert werden.

#### <a name="to-update-a-service-reference"></a>So aktualisieren Sie einen Dienst Verweis

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienst Verweis, und klicken Sie dann auf **Dienst Verweis aktualisieren**.

     Ein Status Dialogfeld wird angezeigt, während der Verweis vom ursprünglichen Speicherort aus aktualisiert wird, und der Dienst Client wird erneut generiert, um alle Änderungen an den Metadaten widerzuspiegeln.

## <a name="removing-a-service-reference"></a>Entfernen eines Dienst Verweises
 Wenn ein Dienst Verweis nicht mehr verwendet wird, können Sie ihn aus der Projekt Mappe entfernen.

#### <a name="to-remove-a-service-reference"></a>So entfernen Sie einen Dienst Verweis

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Dienst Verweis, und klicken Sie dann auf **Löschen**.

     Der Dienst Client wird aus der Projekt Mappe entfernt, und die Metadaten, die den Dienst beschreiben, werden aus der app.config Datei entfernt.

    > [!NOTE]
    > Jeglicher Code, der auf den Dienst Verweis verweist, muss manuell entfernt werden.

## <a name="see-also"></a>Weitere Informationen
 [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
