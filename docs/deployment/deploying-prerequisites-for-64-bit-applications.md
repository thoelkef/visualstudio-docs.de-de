---
title: "Bereitstellen der erforderlichen Komponenten f&#252;r 64-Bit-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 Bit [Visual Studio]"
  - "64-Bit-Anwendungen [Visual Studio]"
  - "64-Bit-Programmierung [Visual Studio]"
  - "Bereitstellen von Anwendungen [Visual Studio], 64 Bit"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bereitstellen der erforderlichen Komponenten f&#252;r 64-Bit-Anwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die ClickOnce\-Bereitstellung unterstützt die Installation von Anwendungen auf 64\-Bit\-Plattformen.  Die Zielplattformen sind **x86** für 32\-Bit\-Plattformen, **x64** für Computer, die die Anweisungssets AMD64 und EM64T unterstützen, und **Itanium** für 64\-Bit\-Itanium\-Prozessoren.  
  
## Voraussetzungen  
 In der folgenden Tabelle sind die verteilbaren Komponenten aufgeführt, die Sie als erforderliche Komponenten für die Installation Ihrer 64\-Bit\-Anwendung verwenden können.  
  
 Wenn Sie eine erforderliche Komponente auswählen, für die keine 64\-Bit\-Komponenten vorhanden sind, wird möglicherweise eine Warnung angezeigt, die darauf hinweist, dass die ausgewählten Pakete für die 64\-Bit\-Plattform nicht verfügbar sind.  
  
|Verteilbare Komponente|x64\-Unterstützung|IA64\-Unterstützung|  
|----------------------------|------------------------|-------------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Ja|Nein|  
|Visual C\+\+ 2010\-Laufzeitbibliotheken \(IA64\)|Nein|Ja|  
|Visual C\+\+ 2010\-Laufzeitbibliotheken \(x64\)|Ja|Nein|  
|Microsoft .NET Framework 4 \(x86 und x64\)|Ja||  
|Microsoft .NET Framework 4 Client Profile \(x86 und x64\)|Ja||  
  
## Siehe auch  
 [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64\-Bit\-Anwendungen](../Topic/64-bit%20Applications.md)