---
title: Dialogfeld "Dienstverweis konfigurieren"
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ed20865726832b57d4d0624d6305daa6ba0fe6fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="configure-service-reference-dialog-box"></a>Dialogfeld "Dienstverweis konfigurieren"

Die **Dienstverweis konfigurieren** Dialogfeld können Sie das Verhalten der Windows Communication Foundation (WCF)-Dienste konfigurieren.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

Für den Zugriff auf die **Dienstverweis konfigurieren** (Dialogfeld), mit der rechten Maustaste, einen Dienst verweisen **Projektmappen-Explorer** , und wählen Sie **Dienstverweis konfigurieren**. Sie können auch das Dialogfeld zugreifen, indem Sie auf die **erweitert** Schaltfläche der **hinzufügen Dienst Dialogfelds "Verweis"**.

## <a name="task-list"></a>Aufgabenliste

- Um die Adresse zu ändern, in denen ein WCF-Dienst gehostet wird, geben Sie die neue Adresse in der **Adresse** Feld.

- Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein zugriffsebenenschlüsselwort in der **Zugriffsebene für generierte Klassen** Liste.

- Um die Methoden eines WCF-Diensts asynchron aufzurufen, wählen Sie die **asynchrone Vorgänge generieren** Kontrollkästchen.

- Wählen Sie zum Generieren von Meldungsvertragstypen in einem WCF-Client die **Meldungsverträge immer generieren** Kontrollkästchen.

- Wählen Sie zum Angeben von Liste oder Wörterbuchauflistungstypen für einen WCF-Client die Typen aus den **"Sammlung"** und **Wörterbuchauflistungstyp** aufgeführt.

- Deaktivieren Sie zum Deaktivieren der Typfreigabe das **Typen in Assemblys verwiesen wird, wiederverwenden** Kontrollkästchen. Zum Aktivieren der Typfreigabe für eine Teilmenge an referenzierten Assemblys wählen die **Typen in Assemblys verwiesen wird, wiederverwenden** Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, und wählen Sie den gewünschten verweist der **referenzierte Assemblyliste**.

## <a name="uielement-list"></a>UIElement-Liste

 **Adresse**

 Wird zum Aktualisieren der Webadresse verwendet, wo ein Dienstverweis nach einem Dienst sucht. Beispielsweise wird während der Entwicklung der Dienst möglicherweise auf einem Entwicklungsserver gehostet und später auf einen Produktionsserver verschoben, was eine Adressenänderung erfordert.

> [!NOTE]
> Das adressenelement ist nicht verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **hinzufügen Dienst Dialogfelds "Verweis"**.

 **Zugriffsebene für generierte Klassen**

 Bestimmt die Codezugriffsebene für WCF-Clientklassen.

> [!NOTE]
> Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md).

 **Asynchrone Vorgänge generieren**

 Bestimmt, ob WCF-Dienstmethoden synchron (standardmäßig) oder asynchron aufgerufen werden.

 **Aufgabenbasierte Vorgänge generieren**

 Beim Schreiben von asynchronem Code können Sie mit dieser Option von der in .Net 4 eingeführten Task Parallel Library (TPL) profitieren. Finden Sie unter [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Meldungsverträge immer generieren**

 Bestimmt, ob Meldungsvertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Nachrichtenverträgen finden Sie unter [Verwendung von Nachrichtenverträgen](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **"Sammlung"**

 Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.

 **Wörterbuchauflistungstyp**

 Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.

 **Typen in Assemblys verwiesen wird, wiederverwenden**

 Bestimmt, ob ein WCF-Client versucht, die in den referenzierten Assemblys bereits vorhandenen Elemente erneut zu verwenden, anstelle neue Typen zu generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.

 **Typen in allen Assemblys verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option alle Typen in der **referenzierte Assemblyliste** wird nach Möglichkeit wiederverwendet werden. Diese Option ist standardmäßig ausgewählt.

 **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**

 Bei Auswahl dieser Option nur die ausgewählten Typen in der **referenzierte Assemblyliste** wiederverwendet.

 **Liste der referenzierten Assemblys**

 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website. Wenn **Typen in Assemblys, auf die verwiesen wird, wiederverwenden** ausgewählt ist, einzelne Assemblys aktiviert oder deaktiviert werden können.

 **Webverweis hinzufügen**

 Zeigt das Dialogfeld "Webverweis hinzufügen".

> [!NOTE]
> Diese Option sollte für Projekte verwendet werden, die Version 2.0 von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vorgeben.

> [!NOTE]
> Die **Webverweis hinzufügen** Schaltfläche ist nur verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **hinzufügen Dienst Dialogfelds "Verweis"**.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Hinzufügen eines Verweises auf einen Webdienst](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)