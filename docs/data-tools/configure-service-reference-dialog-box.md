---
title: Dienstverweis konfigurieren (Dialogfeld)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b622fc77884acde5b81d886628afce9f077e86a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567972"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)

Die **Dienstverweis konfigurieren** Dialogfeld können Sie das Verhalten von Windows Communication Foundation (WCF)-Services zu konfigurieren.

Klicken Sie mit der rechten Maustaste auf einen Dienstverweis im **Projektmappen-Explorer**, und wählen Sie **Dienstverweis konfigurieren** aus, um auf das Dialogfeld **Dienstverweis konfigurieren** zuzugreifen. Sie können auch auf das Dialogfeld zugreifen, indem Sie im Dialogfeld **Dienstverweis hinzufügen** auf die Schaltfläche **Erweitert** klicken.

## <a name="task-list"></a>Aufgabenliste

- Geben Sie zum Ändern der Adresse, unter der ein WCF-Dienst gehostet wird, die neue Adresse in das Feld **Adresse** ein.

- Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein Zugriffsebenenschlüsselwort in der Liste **Zugriffsebene für generierte Klassen** aus.

- Aktivieren Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts das Kontrollkästchen **Asynchrone Vorgänge generieren**.

- Aktivieren Sie zum Generieren von Nachrichtenvertragstypen in einem WCF-Client das Kontrollkästchen **Meldungsverträge immer generieren**.

- Wählen Sie die Typen aus den Listen **Sammlungstyp** und **Wörterbuchsammlungstyp** aus, um Listen- oder Wörterbuchsammlungstypen für einen WCF-Client anzugeben.

- Deaktivieren Sie das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, um die Typfreigabe zu deaktivieren. Aktivieren Sie zum Aktivieren der Typfreigabe für eine Teilmenge an referenzierten Assemblys das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, klicken Sie auf **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**, und wählen Sie die gewünschten Verweise in der Liste **Assemblys, auf die verwiesen wird** aus.

## <a name="uielement-list"></a>UIElement-Liste

 **Address**

 Aktualisiert die Webadresse, wo ein Dienstverweis für einen Dienst sucht. Z. B. während der Entwicklung der Dienst kann sein, die auf einem Entwicklungsserver gehostet und dann später auf einem Produktionsserver, die eine adressenänderung verschoben.

> [!NOTE]
> Das Adressenelement ist nicht verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld **Dienstverweis hinzufügen** angezeigt wird.

 **Zugriffsebene für generierte Klassen**

 Bestimmt die Codezugriffsebene für WCF-Clientklassen.

> [!NOTE]
> Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Troubleshooting service references (Problembehandlung bei Dienstverweisen)](../data-tools/troubleshooting-service-references.md).

 **Asynchrone Vorgänge generieren**

 Bestimmt, ob der WCF-Dienstmethoden synchron aufgerufen wird (Standard) oder asynchron.

 **Aufgabenbasierte Vorgänge generieren**

 Beim Schreiben von asynchronem Code, Sie können diese Option profitieren Sie von der Task Parallel Library (TPL), die eingeführt wurde mit .NET 4. Finden Sie unter [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Meldungsverträge immer generieren**

 Bestimmt, ob Meldungsvertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Nachrichtenverträgen finden Sie unter[Using message contracts (Verwendung von Nachrichtenverträgen)](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Sammlungstyp**

 Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.

 **Wörterbuchsammlungstyp**

 Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.

 **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**

 Bestimmt, ob ein WCF-Client versucht, erneut verwenden, was bereits vorhanden ist, in Assemblys verwiesen wird, anstatt neue Typen generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.

 **Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option alle Typen in der **referenzierte Assemblyliste** nach Möglichkeit wiederverwendet werden. Diese Option ist standardmäßig ausgewählt.

 **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option nur die ausgewählten Typen in der **referenzierte Assemblyliste** wiederverwendet werden.

 **Liste „Assemblys, auf die verwiesen wird“**

 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website. Bei der Auswahl **Typen in referenzierten Assemblys wiederverwenden**, können Sie aktivieren bzw. deaktivieren Sie einzelne Assemblys.

 **Webverweis hinzufügen**

 Zeigt das Dialogfeld **Webverweis hinzufügen** an.

> [!NOTE]
> Diese Option sollte nur verwendet werden, für Projekte, die als Version 2.0 von Ziel der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
>
> [!NOTE]
> Die **Webverweis hinzufügen** Schaltfläche ist nur verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Fügen Sie einen Verweis auf einen Webdienst](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)