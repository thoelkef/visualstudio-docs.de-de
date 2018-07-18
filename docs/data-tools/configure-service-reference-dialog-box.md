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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 93d39aedc04cbdaebc35c892a8393ca394f44898
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281065"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)

Die **Dienstverweis konfigurieren** Dialogfeld können Sie das Verhalten von Windows Communication Foundation (WCF)-Services zu konfigurieren.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

Für den Zugriff auf die **Dienstverweis konfigurieren** verweisen Sie im Dialogfeld mit der rechten Maustaste ein Dienst in **Projektmappen-Explorer** , und wählen Sie **Dienstverweis konfigurieren**. Sie können auch das Dialogfeld zugreifen, indem Sie auf die **erweitert** Schaltfläche der **Add Service Reference Dialog Box**.

## <a name="task-list"></a>Aufgabenliste

- Um die Adresse zu ändern, in dem ein WCF-Dienst gehostet wird, geben Sie auf die neue Adresse in der **Adresse** Feld.

- Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein zugriffsebenenschlüsselwort in der **Zugriffsebene für generierte Klassen** Liste.

- Wählen Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts die **asynchrone Vorgänge generieren** Kontrollkästchen.

- Wählen Sie zum Generieren von Meldungsvertragstypen in einem WCF-Client die **Meldungsverträge immer generieren** Kontrollkästchen.

- Wählen Sie zum Angeben von Listen oder Wörterbuchauflistungstypen Auflistungstypen für einen WCF-Client die Typen aus den **Auflistungstyp** und **Wörterbuchauflistungstyp** aufgeführt.

- Deaktivieren Sie zum Deaktivieren der Typfreigabe das **Typen in referenzierten Assemblys wiederverwenden** Kontrollkästchen. Um die Typfreigabe für eine Teilmenge an referenzierten Assemblys zu aktivieren, wählen die **Typen in referenzierten Assemblys wiederverwenden** aktivieren Sie das Kontrollkästchen **Typen in referenzierten Assemblys wiederverwenden**, und wählen Sie den gewünschten verweist auf die **referenzierte Assemblyliste**.

## <a name="uielement-list"></a>UIElement-Liste

 **Adresse**

 Aktualisiert die Webadresse, wo ein Dienstverweis für einen Dienst sucht. Z. B. während der Entwicklung der Dienst kann sein, die auf einem Entwicklungsserver gehostet und dann später auf einem Produktionsserver, die eine adressenänderung verschoben.

> [!NOTE]
> Das adressenelement ist nicht verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.

 **Zugriffsebene für generierte Klassen**

 Bestimmt die Codezugriffsebene für WCF-Clientklassen.

> [!NOTE]
> Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md).

 **Asynchrone Vorgänge generieren**

 Bestimmt, ob der WCF-Dienstmethoden synchron aufgerufen wird (Standard) oder asynchron.

 **Aufgabenbasierte Vorgänge generieren**

 Beim Schreiben von asynchronem Code, Sie können diese Option profitieren Sie von der Task Parallel Library (TPL), die eingeführt wurde mit .NET 4. Finden Sie unter [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Meldungsverträge immer generieren**

 Bestimmt, ob Meldungsvertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Meldungsverträgen finden Sie unter [Verwenden von Nachrichtenverträgen](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Auflistungstyp**

 Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.

 **Wörterbuchauflistungstyp**

 Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.

 **Typen in referenzierten Assemblys wiederverwenden**

 Bestimmt, ob ein WCF-Client versucht, erneut verwenden, was bereits vorhanden ist, in Assemblys verwiesen wird, anstatt neue Typen generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.

 **Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option alle Typen in der **referenzierte Assemblyliste** nach Möglichkeit wiederverwendet werden. Diese Option ist standardmäßig ausgewählt.

 **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option nur die ausgewählten Typen in der **referenzierte Assemblyliste** wiederverwendet werden.

 **Liste der referenzierten Assemblys**

 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website. Bei der Auswahl **Typen in referenzierten Assemblys wiederverwenden**, können Sie aktivieren bzw. deaktivieren Sie einzelne Assemblys.

 **Webverweis hinzufügen**

 Zeigt die **Webverweis hinzufügen** Dialogfeld.

> [!NOTE]
> Diese Option sollte nur verwendet werden, für Projekte, die als Version 2.0 von Ziel der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> Die **Webverweis hinzufügen** Schaltfläche ist nur verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Hinzufügen eines Verweises auf einen Webdienst](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)