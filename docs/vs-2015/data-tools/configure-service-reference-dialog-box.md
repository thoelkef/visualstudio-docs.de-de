---
title: Konfigurieren der Service-Dialogfelds "Verweis" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 60a1c7a057495b89aa8923d424fb09d9ecb1c232
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512142"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Configure Service Reference Dialog Box](https://docs.microsoft.com/visualstudio/data-tools/configure-service-reference-dialog-box).  
  
  
Die **Dienstverweis konfigurieren** Dialogfeld können Sie so konfigurieren Sie das Verhalten der [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Dienste.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Für den Zugriff auf die **Dienstverweis konfigurieren** verweisen Sie im Dialogfeld mit der rechten Maustaste ein Dienst in **Projektmappen-Explorer** , und wählen Sie **Dienstverweis konfigurieren**. Sie können auch das Dialogfeld zugreifen, indem Sie auf die **erweitert** Schaltfläche der **Add Service Reference Dialog Box**.  
  
## <a name="task-list"></a>Aufgabenliste  
  
-   Um die Adresse zu ändern, in dem ein WCF-Dienst gehostet wird, geben Sie auf die neue Adresse in der **Adresse** Feld.  
  
-   Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein zugriffsebenenschlüsselwort in der **Zugriffsebene für generierte Klassen** Liste.  
  
-   Wählen Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts die **asynchrone Vorgänge generieren** Kontrollkästchen.  
  
-   Wählen Sie zum Generieren von Meldungsvertragstypen in einem WCF-Client die **Meldungsverträge immer generieren** Kontrollkästchen.  
  
-   Wählen Sie zum Angeben von Listen oder Wörterbuchauflistungstypen Auflistungstypen für einen WCF-Client die Typen aus den **Auflistungstyp** und **Wörterbuchauflistungstyp** aufgeführt.  
  
-   Deaktivieren Sie zum Deaktivieren der Typfreigabe das **Typen in referenzierten Assemblys wiederverwenden** Kontrollkästchen. Um die Typfreigabe für eine Teilmenge an referenzierten Assemblys zu aktivieren, wählen die **Typen in referenzierten Assemblys wiederverwenden** aktivieren Sie das Kontrollkästchen **Typen in referenzierten Assemblys wiederverwenden**, und wählen Sie den gewünschten verweist auf die **referenzierte Assemblyliste**.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Adresse**  
 Wird zum Aktualisieren der Webadresse verwendet, wo ein Dienstverweis nach einem Dienst sucht. Beispielsweise wird während der Entwicklung der Dienst möglicherweise auf einem Entwicklungsserver gehostet und später auf einen Produktionsserver verschoben, was eine Adressenänderung erfordert.  
  
> [!NOTE]
>  Das adressenelement ist nicht verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.  
  
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
  
 **Auflistungstyp**  
 Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.  
  
 **Wörterbuchauflistungstyp**  
 Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Typen in referenzierten Assemblys wiederverwenden**  
 Bestimmt, ob ein WCF-Client versucht, die in den referenzierten Assemblys bereits vorhandenen Elemente erneut zu verwenden, anstelle neue Typen zu generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird. Diese Option ist standardmäßig aktiviert.  
  
 **Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl dieser Option alle Typen in der **referenzierte Assemblyliste** wird nach Möglichkeit wiederverwendet werden. Diese Option ist standardmäßig ausgewählt.  
  
 **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl dieser Option nur die ausgewählten Typen in der **referenzierte Assemblyliste** wiederverwendet.  
  
 **Liste der referenzierten Assemblys**  
 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website. Wenn **Typen in referenzierten Assemblys wiederverwenden** ausgewählt ist, einzelne Assemblys aktiviert oder deaktiviert werden können.  
  
 **Webverweis hinzufügen**  
 Zeigt die [NIB: Hinzufügen von Web-Dialogfelds "Verweis"](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Diese Option sollte für Projekte verwendet werden, die Version 2.0 von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vorgeben.  
  
> [!NOTE]
>  Die **Webverweis hinzufügen** Schaltfläche ist nur verfügbar, wenn die **Dienstverweis konfigurieren** Dialogfeld wird angezeigt, aus der **Add Service Reference Dialog Box**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: hinzufügen, aktualisieren oder Entfernen eines Dienstverweises](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Vorgehensweise: Hinzufügen eines Verweises auf einen Webdienst](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

