---
title: "Die Proxyeinstellungen auf diesem Computer sind nicht richtig zur Websuche konfiguriert. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_MUSTSPECIFYPROXYSERVER"
  - "vs.WebDiscoveryProxyHelp"
ms.assetid: aea2cc20-9180-47cb-b1ed-78fa5f8a407f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Proxyeinstellungen auf diesem Computer sind nicht richtig zur Websuche konfiguriert.
Dieser Fehler wird im Dialogfeld „Webverweis hinzufügen“ angezeigt, wenn Sie auf einem Computer entwickeln, der sich hinter einer Firewall befindet, und kein Proxyserver explizit für Internet Explorer\-Verbindungen angegeben wurde. Sie müssen explizit die Adresse und den Port des Proxyservers im Netzwerk angeben, um Dienste außerhalb der Firewall dem Webbrowser im Dialogfeld „Webverweis hinzufügen“ verfügbar zu machen. Die Proxyoption der automatischen Erkennung für Internet Explorer\-Verbindungen wird von .NET Framework ignoriert. Sie müssen diese Proxyinformationen vielleicht bei Ihrem Netzwerkadministrator erfragen.  
  
 Weitere Informationen über „Automatic Discovery for Firewall and Web Proxy Clients“ \(Automatische Erkennung für Firewall\- und Webproxyclients\) finden Sie unter: [http:\/\/www.microsoft.com\/technet\/prodtechnol\/isa\/2004\/plan\/automaticdiscovery.mspx](http://www.microsoft.com/technet/prodtechnol/isa/2004/plan/automaticdiscovery.mspx).  
  
### So geben Sie einen Proxyserver für Internet Explorer an  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  Wählen Sie im Dialogfeld **Optionen** die Option **Umgebung** und dann **Webbrowser** aus.  
  
3.  Klicken Sie auf **Internet Explorer\-Optionen**.  
  
4.  Klicken Sie auf der Registerkarte **Verbindungen** auf **LAN\-Einstellungen**.  
  
5.  Heben Sie die Auswahl **Einstellungen automatisch ermitteln** auf.  
  
6.  Wählen Sie im Bereich **Proxyserver** die Option **Proxyserver für LAN verwenden \(diese Einstellungen gelten nicht für VPN\- oder Einwählverbindungen\)**.  
  
7.  Geben Sie die Adresse und Portnummer an, die Ihrem Netzwerk entsprechen.  
  
8.  Klicken Sie auf **OK**, auf **OK** und dann nochmals auf **OK**.  
  
9. Wählen Sie aus dem Menü **Datei** die Option **Beenden**, und öffnen Sie Visual Studio erneut.  
  
## Siehe auch  
 [NIB: Dialogfeld "Webverweis hinzufügen"](http://msdn.microsoft.com/de-de/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [NIB: Hinzufügen und Entfernen von Webverweisen](http://msdn.microsoft.com/de-de/a7ddaa5d-4672-405b-91b3-39de65d7e3a2)   
 [Programming the Web with XML Web Services](http://msdn.microsoft.com/de-de/2d651a26-73df-4b39-85fa-7913a7d6bee4)