---
title: "Dialogfeld &quot;Dienstverweis konfigurieren&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "WCF-Dienste, Dienstverweis konfigurieren (Dialogfeld)"
  - "Dienstverweise [Visual Studio], Konfigurieren des Verhaltens"
  - "Dienstverweis konfigurieren (Dialogfeld)"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dialogfeld &quot;Dienstverweis konfigurieren&quot;
Das Dialogfeld **Dienstverweis konfigurieren** ermöglicht Ihnen, das Verhalten der [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]\-Dienste zu konfigurieren.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Klicken Sie mit der rechten Maustaste auf einen Dienstverweis im **Projektmappen\-Explorer**, und wählen Sie **Dienstverweis konfigurieren** aus, um auf das Dialogfeld **Dienstverweis konfigurieren** zuzugreifen.  Sie können auch auf das Dialogfeld zugreifen, indem Sie im Dialogfeld [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)auf die Schaltfläche **Erweitert** klicken.  
  
## Aufgabenliste  
  
-   Geben Sie zum Ändern der Adresse, unter der ein WCF\-Dienst gehostet wird, die neue Adresse in das Feld **Adresse** ein.  
  
-   Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF\-Client ein Zugriffsebenenschlüsselwort in der Liste **Zugriffsebene für generierte Klassen** aus.  
  
-   Aktivieren Sie zum asynchronen Aufrufen der Methoden eines WCF\-Diensts das Kontrollkästchen **Asynchrone Vorgänge generieren**.  
  
-   Aktivieren Sie zum Generieren von Meldungsvertragstypen in einem WCF\-Client das Kontrollkästchen **Meldungsverträge immer generieren**.  
  
-   Wählen Sie zum Angeben einer von Listen oder Wörterbuchauflistungstypen für einen WCF\-Client die Typen aus den Listen **Auflistungstyp** und **Wörterbuchauflistungstyp** aus.  
  
-   Deaktivieren Sie zum Deaktivieren der Typfreigabe das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**.  Aktivieren Sie zum Auswählen der Typfreigabe für eine Teilmenge an referenzierten Assemblys das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**, wählen Sie **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden** aus, und wählen Sie die gewünschten Verweise in der Liste **Referenzierte Assemblys** aus.  
  
## UIElement-Liste  
 **Adresse**  
 Wird zum Aktualisieren der Webadresse verwendet, wo ein Dienstverweis nach einem Dienst sucht.  Beispielsweise wird während der Entwicklung der Dienst möglicherweise auf einem Entwicklungsserver gehostet und später auf einen Produktionsserver verschoben, was eine Adressenänderung erfordert.  
  
> [!NOTE]
>  Das Adressenelement ist nicht verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md) angezeigt wird.  
  
 **Zugriffsebene für generierte Klassen**  
 Bestimmt die Codezugriffsebene für WCF\-Clientklassen.  
  
> [!NOTE]
>  Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden.  Weitere Informationen finden Sie unter [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
 **Asynchrone Vorgänge generieren**  
 Bestimmt, ob WCF\-Dienstmethoden synchron \(standardmäßig\) oder asynchron aufgerufen werden.  
  
 **Aufgabenbasierte Vorgänge generieren**  
 Beim Schreiben von asynchronem Code können Sie mit dieser Option von der in .Net 4 eingeführten Task Parallel Library \(TPL\) profitieren.  Siehe dazu [Task Parallel Library \(TPL\)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Meldungsverträge immer generieren**  
 Bestimmt, ob Meldungsvertragstypen für einen WCF\-Client generiert werden.  Weitere Informationen zu Nachrichtenverträgen finden Sie unter [Verwendung von Nachrichtenverträgen](../Topic/Using%20Message%20Contracts.md).  
  
 **Auflistungstyp**  
 Gibt den Listenauflistungstyp für einen WCF\-Client an.  Der Standardtyp ist <xref:System.Array>.  
  
 **Wörterbuchauflistungstyp**  
 Gibt den Wörterbuchauflistungstyp für einen WCF\-Client an.  Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Typen in Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bestimmt, ob ein WCF\-Client versucht, die in den referenzierten Assemblys bereits vorhandenen Elemente erneut zu verwenden, anstelle neue Typen zu generieren, wenn ein Dienst hinzugefügt oder aktualisiert wird.  Diese Option ist standardmäßig aktiviert.  
  
 **Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl werden alle Typen in der Liste **Assemblys, auf die verwiesen wird** nach Möglichkeit wiederverwendet.  Diese Option ist standardmäßig ausgewählt.  
  
 **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**  
 Bei Auswahl werden nur die ausgewählten Typen in der Liste **Assemblys, auf die verwiesen wird** wiederverwendet.  
  
 **Liste "Assemblys, auf die verwiesen wird"**  
 Enthält eine Liste von referenzierten Assemblys für das Projekt oder die Website.  Wenn **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden** ausgewählt ist, können einzelne Assemblys aktiviert oder deaktiviert werden.  
  
 **Webverweis hinzufügen**  
 Zeigt das Dialogfeld [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/de-de/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) an.  
  
> [!NOTE]
>  Diese Option sollte für Projekte verwendet werden, die Version 2.0 von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vorgeben.  
  
> [!NOTE]
>  Die Schaltfläche **Webverweis hinzufügen** ist nur verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md) angezeigt wird.  
  
## Siehe auch  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Windows Communication Foundation\-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)   
 [Beispiel für das Nutzen von ASMX\- und WCF\-Diensten](http://msdn.microsoft.com/de-de/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)