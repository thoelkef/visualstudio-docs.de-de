---
title: "How to: Specify Verbose Log Files for ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "logs, ClickOnce deployment"
  - "ClickOnce deployment, logging"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Specify Verbose Log Files for ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet Aktivitätsprotokolldateien für alle Bereitstellungen.  Diese Protokolle enthalten Details zum Installieren, Initialisieren, Aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung.  Um die Ausführlichkeit der Daten zu erhöhen, die von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in die Protokolldateien geschrieben werden, geben Sie den Ausführlichkeitsgrad mithilfe des Registrierungs\-Editors \(**regedit.exe**\) an.  
  
> [!CAUTION]
>  Die unsachgemäße Verwendung des Registrierungs\-Editors kann ernste Probleme verursachen und u. U. eine Neuinstallation des Betriebssystems erforderlich machen.  Die Verwendung des Registrierungs\-Editors erfolgt auf eigenes Risiko.  
  
 Im folgenden Verfahren wird beschrieben, wie der Ausführlichkeitsgrad von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Protokolldateien für den aktuellen Benutzer angegeben wird.  Um den Ausführlichkeitsgrad zu verringern, entfernen Sie diesen Registrierungswert.  
  
### So geben Sie ausführliche Protokolldateien an  
  
1.  Öffnen Sie **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKEY_CURRENT_USERSoftware\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Erstellen Sie ggf. einen neuen Zeichenfolgenwert mit dem Namen `LogVerbosityLevel`.  
  
4.  Legen Sie den `LogVerbosityLevel`\-Wert auf `1` fest.  
  
## Siehe auch  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)