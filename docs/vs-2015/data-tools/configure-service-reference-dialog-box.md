---
title: Konfigurieren der Service-Dialogfelds "Verweis" | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4cc4ae6704f59f33de091fe528c7e05898361115
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957835"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die **Dienstverweis konfigurieren** Dialogfeld können Sie so konfigurieren Sie das Verhalten der [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Dienste.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Klicken Sie mit der rechten Maustaste auf einen Dienstverweis im **Projektmappen-Explorer**, und wählen Sie **Dienstverweis konfigurieren** aus, um auf das Dialogfeld **Dienstverweis konfigurieren** zuzugreifen. Sie können auch auf das Dialogfeld zugreifen, indem Sie im Dialogfeld **Dienstverweis hinzufügen** auf die Schaltfläche **Erweitert** klicken.  
  
## <a name="task-list"></a>Aufgabenliste  
  
-   Geben Sie zum Ändern der Adresse, unter der ein WCF-Dienst gehostet wird, die neue Adresse in das Feld **Adresse** ein.  
  
-   Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein Zugriffsebenenschlüsselwort in der Liste **Zugriffsebene für generierte Klassen** aus.  
  
-   Aktivieren Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts das Kontrollkästchen **Asynchrone Vorgänge generieren**.  
  
-   Aktivieren Sie zum Generieren von Nachrichtenvertragstypen in einem WCF-Client das Kontrollkästchen **Meldungsverträge immer generieren**.  
  
-   Wählen Sie die Typen aus den Listen **Sammlungstyp** und **Wörterbuchsammlungstyp** aus, um Listen- oder Wörterbuchsammlungstypen für einen WCF-Client anzugeben.  
  
-   Deaktivieren Sie das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, um die Typfreigabe zu deaktivieren. Aktivieren Sie zum Aktivieren der Typfreigabe für eine Teilmenge an referenzierten Assemblys das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, klicken Sie auf **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**, und wählen Sie die gewünschten Verweise in der Liste **Assemblys, auf die verwiesen wird** aus.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Address**  
 Wird zum Aktualisieren der Webadresse verwendet, wo ein Dienstverweis nach einem Dienst sucht. Beispielsweise wird während der Entwicklung der Dienst möglicherweise auf einem Entwicklungsserver gehostet und später auf einen Produktionsserver verschoben, was eine Adressenänderung erfordert.  
  
> [!NOTE]
>  Das Adressenelement ist nicht verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld **Dienstverweis hinzufügen** angezeigt wird.  
  
 **Zugriffsebene für generierte Klassen**  
 Bestimmt die Codezugriffsebene für WCF-Clientklassen.  
  
> [!NOTE]
>  Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md).  
  
 **Asynchrone Vorgänge generieren**  
 Bestimmt, ob WCF-Dienstmethoden synchron (standardmäßig) oder asynchron aufgerufen werden.  
  
 **Aufgabenbasierte Vorgänge generieren**  
 Beim Schreiben von asynchronem Code können Sie mit dieser Option von der in .Net 4 eingeführten Task Parallel Library (TPL) profitieren. Finden Sie unter [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Meldungsverträge immer generieren**  
 Bestimmt, ob Meldungsvertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Meldungsverträgen finden Sie unter [Using Message Contracts](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Sammlungstyp**  
 Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.  
  
 **Wörterbuchsammlungstyp**  
 Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bestimmt, ob ein WCF-Client versucht, die in den referenzierten Assemblys bereits vorhandenen Elemente erneut zu verwenden, anstelle neue Typen zu generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.  
  
 **Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl dieser Option alle Typen in der **referenzierte Assemblyliste** wird nach Möglichkeit wiederverwendet werden. Diese Option ist standardmäßig ausgewählt.  
  
 **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl dieser Option nur die ausgewählten Typen in der **referenzierte Assemblyliste** wiederverwendet.  
  
 **Liste „Assemblys, auf die verwiesen wird“**  
 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website. Wenn **Typen in referenzierten Assemblys wiederverwenden** ausgewählt ist, einzelne Assemblys aktiviert oder deaktiviert werden können.  
  
 **Webverweis hinzufügen**  
 Zeigt die [NIB: Fügen Sie im Dialogfeld "Verweis" Web](http://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Diese Option sollte für Projekte verwendet werden, die Version 2.0 von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vorgeben.  
  
> [!NOTE]
>  Die **Webverweis hinzufügen** Schaltfläche ist nur verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Hinzufügen, aktualisieren oder Entfernen eines Dienstverweises](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Vorgehensweise: Fügen Sie einen Verweis auf einen Webdienst](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
