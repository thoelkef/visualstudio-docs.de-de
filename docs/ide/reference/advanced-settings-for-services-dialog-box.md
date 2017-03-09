---
title: "Dialogfeld &quot;Erweiterte Einstellungen f&#252;r Dienste&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedServices"
helpviewer_keywords: 
  - "Dialogfeld Erweiterte Einstellungen für Dienste"
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dialogfeld &quot;Erweiterte Einstellungen f&#252;r Dienste&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Clientanwendungsdienste ermöglichen den vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)]\-Anmeldung, \-Rollen und \-Profildienste aus Windows Forms und Windows Presentation Foundation \(WPF\)\-Anwendungen.  Sie können Clientanwendungsdienste auf der Seite **Dienste** des **Projekt\-Designers** konfigurieren.  Weitere Informationen zur Seite **Dienste** finden Sie unter [Services\-Seite, Projekt\-Designer](../../ide/reference/services-page-project-designer.md).  
  
 Im Dialogfeld **Erweiterte Einstellungen für Dienste** der Seite **Dienste** des **Projekt\-Designers** können Sie erweiterte Einstellungen für Clientanwendungsdienste konfigurieren.  Mit diesen Einstellungen können Sie einige Standardverhaltensweisen von Anwendungsdiensten überschreiben, um weniger gängige Szenarien zu ermöglichen.  Weitere Informationen finden Sie unter [Clientanwendungsdienste](../Topic/Client%20Application%20Services.md).  
  
 Wählen Sie zum Aufrufen des Dialogfelds **Erweiterte Einstellungen für Dienste** einen Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Wird der **Projekt\-Designer** angezeigt, klicken Sie auf die Registerkarte **Dienste** und dann auf die Schaltfläche **Erweitert**.  Diese Schaltfläche ist so lange deaktiviert, bis Sie Clientanwendungsdienste aktivieren.  
  
## Aufgabenliste  
 [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)  
  
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/de-de/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## UIElement-Liste  
 **Kennworthash lokal speichern, um Offlineanmeldung zu ermöglichen**  
 Gibt an, ob das Benutzerkennwort in verschlüsselter Form lokal zwischengespeichert wird, damit der Benutzer sich anmelden kann, während die Anwendung im Offlinemodus ist.  Weitere Informationen finden Sie unter [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/de-de/f792cb16-8520-4a0f-9dc9-07bfbc454e38).  Diese Option ist standardmäßig aktiviert.  
  
 **Erneute Benutzeranmeldung bei Ablauf des Cookies anfordern**  
 Gibt an, ob bereits authentifizierte Benutzer automatisch erneut authentifiziert werden, wenn die Anwendung auf den Rollen\- oder Profildienst zugreift und das Authentifizierungscookie für den Server abgelaufen ist.  Wählen Sie diese Option aus, um Zugriff auf die Anwendungsdienste zu verweigern und explizites erneutes Authentifizieren zu erfordern, nachdem das Cookie abgelaufen ist.  Diese Option ist hilfreich für Anwendungen, die an öffentlichen Speicherorten bereitgestellt werden, um sicherzustellen, dass Anwender, die die Anwendung nach Gebrauch aktiviert lassen, nicht unbegrenzt lange authentifiziert bleiben.  Diese Option ist standardmäßig deaktiviert.  
  
 **Cachetimeout des Rollendiensts**  
 Gibt an, für welche Dauer der Clientrollenanbieter zwischengespeicherte Rollenwerte verwendet, anstatt auf den Rollendienst zuzugreifen.  Legen Sie dieses Zeitintervall auf einen kleinen Wert fest, wenn Rollen häufig aktualisiert werden, bzw. auf einen größeren Wert, wenn Rollen selten aktualisiert werden.  Der Standardwert ist ein Tag.  
  
 Der Rollenanbieter greift auf die zwischengespeicherten Rollenwerte oder den Rollendienst zu, wenn Sie die <xref:System.Web.Security.RolePrincipal.IsInRole%2A>\-Methode aufrufen.  Um den Cache programmgesteuert zu löschen und den Zugriff auf den Remotedienst durch diese Methode zu erzwingen, rufen Sie die <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>\-Methode auf.  
  
 **Benutzerdefinierte Verbindungszeichenfolge verwenden**  
 Gibt an, ob die Clientdienstanbieter einen benutzerdefinierten Datenspeicher für den lokalen Cache verwenden.  Standardmäßig verwenden die Dienstanbieter das lokale Dateisystem für den Cache.  Ist diese Option ausgewählt, wird das Textfeld automatisch mit einer Standardverbindungszeichenfolge gefüllt.  Sie können die Standardverbindungszeichenfolge beibehalten, damit automatisch eine SQL Server Compact Edition\-Datenbank erstellt und verwendet wird, oder Sie können eine Verbindungszeichenfolge für eine vorhandene SQL Server\-Datenbank angeben.  Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md).  Diese Option ist standardmäßig deaktiviert.  
  
## Siehe auch  
 [Clientanwendungsdienste](../Topic/Client%20Application%20Services.md)   
 [Services\-Seite, Projekt\-Designer](../../ide/reference/services-page-project-designer.md)   
 [Gewusst wie: Konfigurieren von Clientanwendungsdiensten](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)   
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/de-de/f792cb16-8520-4a0f-9dc9-07bfbc454e38)