---
title: "Fehler: Firewall und &quot;Keine Authentifizierung&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.noauth"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Firewall und &quot;Keine Authentifizierung&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Internetverbindungsfirewall auf dem Remotecomputer wurde nicht für das Remotedebuggen eingerichtet.  Für das Remotedebuggen mit `No Authentication` muss der Ausnahmenliste die Datei msvsmon.exe hinzugefügt werden.  Es ist möglicherweise auch erforderlich, einige IPSEC\-Anschlüsse zu öffnen.  
  
> [!NOTE]
>  Der Remotedebugger kann die Windows Firewall automatisch konfigurieren.  Wenn eine andere Firewall als die Windows Firewall verwendet wird, wie z. B. eine Software\- oder Hardwarefirewall eines Drittanbieters, muss die Firewall manuell konfiguriert werden, um das Remotedebugging zu ermöglichen.  Lassen Sie hierzu Verkehr für die TCP\/IP\-Ports zu, die von msvsmon.exe abgehört werden.  Standardmäßig handelt es sich hierbei um Ports 4018 und 4019, wobei 4018 auf allen Betriebssystemen und 4019 wird nur unter Windows x64 verwendet wird, um Debugging von x86\-Prozessen zu ermöglichen.  
  
 Weitere Informationen finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).