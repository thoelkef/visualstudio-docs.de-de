---
title: Dialog Feld "Dienst Verweis konfigurieren" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651110"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Dialogfeld **Dienst Verweis konfigurieren** können Sie das Verhalten von [!INCLUDE[vsindigo](../includes/vsindigo-md.md)]-Diensten konfigurieren.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Klicken Sie mit der rechten Maustaste auf einen Dienstverweis im **Projektmappen-Explorer**, und wählen Sie **Dienstverweis konfigurieren** aus, um auf das Dialogfeld **Dienstverweis konfigurieren** zuzugreifen. Sie können auch auf das Dialogfeld zugreifen, indem Sie im Dialogfeld **Dienstverweis hinzufügen** auf die Schaltfläche **Erweitert** klicken.

## <a name="task-list"></a>Aufgabenliste

- Geben Sie zum Ändern der Adresse, unter der ein WCF-Dienst gehostet wird, die neue Adresse in das Feld **Adresse** ein.

- Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein Zugriffsebenenschlüsselwort in der Liste **Zugriffsebene für generierte Klassen** aus.

- Aktivieren Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts das Kontrollkästchen **Asynchrone Vorgänge generieren**.

- Aktivieren Sie zum Generieren von Nachrichtenvertragstypen in einem WCF-Client das Kontrollkästchen **Meldungsverträge immer generieren**.

- Wählen Sie die Typen aus den Listen **Sammlungstyp** und **Wörterbuchsammlungstyp** aus, um Listen- oder Wörterbuchsammlungstypen für einen WCF-Client anzugeben.

- Deaktivieren Sie das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, um die Typfreigabe zu deaktivieren. Aktivieren Sie zum Aktivieren der Typfreigabe für eine Teilmenge an referenzierten Assemblys das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, klicken Sie auf **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**, und wählen Sie die gewünschten Verweise in der Liste **Assemblys, auf die verwiesen wird** aus.

## <a name="uielement-list"></a>UIElement-Liste
 **Adresse** Wird verwendet, um die Webadresse zu aktualisieren, in der ein Dienst Verweis nach einem Dienst sucht. Beispielsweise wird während der Entwicklung der Dienst möglicherweise auf einem Entwicklungsserver gehostet und später auf einen Produktionsserver verschoben, was eine Adressenänderung erfordert.

> [!NOTE]
> Das Adressenelement ist nicht verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld **Dienstverweis hinzufügen** angezeigt wird.

 **Zugriffsebene für generierte Klassen** Bestimmt die Code Zugriffsebene für WCF-Client Klassen.

> [!NOTE]
> Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Problembehandlung für Dienst Verweise](../data-tools/troubleshooting-service-references.md).

 **Asynchrone Vorgänge generieren** Bestimmt, ob WCF-Dienst Methoden synchron (Standard) oder asynchron aufgerufen werden.

 **Aufgabenbasierte Vorgänge generieren** Wenn Sie asynchronen Code schreiben, können Sie mit dieser Option die Task Parallel Library (TPL) nutzen, die mit .NET 4 eingeführt wurde. Weitere Informationen finden Sie unter [Task Parallel Library (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Nachrichten Verträge immer generieren** Bestimmt, ob Nachrichten Vertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Nachrichten Verträgen finden Sie unter [Verwenden von Nachrichten Verträgen](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Sammlungstyp** Gibt den Listen Auflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.

 **Wörterbuch Sammlungstyp** Gibt den Wörterbuch Sammlungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.

 **Typen in referenzierten** Assemblys erneut Bestimmt, ob ein WCF-Client wieder verwendet werden soll, der bereits in referenzierten Assemblys vorhanden ist, anstatt neue Typen zu erstellen, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.

 **Typen in allen referenzierten** Assemblys wieder verwenden Wenn diese Option aktiviert ist, werden alle Typen in der Liste Assemblys, auf die **verwiesen** wird, wenn möglich Diese Option ist standardmäßig ausgewählt.

 **Typen in angegebenen referenzierten** Assemblys wieder verwenden Wenn diese Option ausgewählt ist, werden nur die ausgewählten Typen in der Liste der Assemblys, auf die **verwiesen** wird

 **Referenzierte** Assemblys Enthält eine Liste der referenzierten Assemblys für das Projekt oder die Website. Beim Auswählen von **Typen in angegebenen** Assemblys, auf die verwiesen wird, können einzelne Assemblys ausgewählt oder gelöscht werden.

 **Webverweis hinzufügen** Zeigt das [Dialog Feld NIB: Webverweis hinzufügen](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)an.

> [!NOTE]
> Diese Option sollte für Projekte verwendet werden, die Version 2.0 von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vorgeben.

> [!NOTE]
> Die Schaltfläche **Webverweis hinzufügen** ist nur verfügbar, wenn das Dialogfeld **Dienst Verweis konfigurieren** im Dialog **Feld Dienstverweis hinzufügen**angezeigt wird.

## <a name="see-also"></a>Siehe auch
 Vorgehens [Weise: Hinzufügen, aktualisieren oder Entfernen eines Dienst Verweises](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) Gewusst [wie: Hinzufügen eines Verweises auf einen Webdienst](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation Services und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
