---
title: "Logische Operatoren in Suchausdr&#252;cken | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, Logische Suchoperatoren"
  - "Logische Suchoperatoren [Help Viewer 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Logische Operatoren in Suchausdr&#252;cken
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Verwendung der logischen Operatoren können Sie die Suche nach Inhalten weiter eingrenzen, indem Sie komplexere Suchausdrücke aus einfacheren erstellen.  Wie die folgende Tabelle zeigt, geben logische Operatoren an, wie mehrere Suchbegriffe in einer Suchabfrage kombiniert werden sollen.  
  
> [!IMPORTANT]
>  Sie müssen logische Operatoren in Großbuchstaben eingeben, damit das Suchmodul diese erkennt.  
  
|So suchen Sie|Verwendung|Beispiel|Ergebnis|  
|-------------------|----------------|--------------|--------------|  
|Beide Bedingungen im selben Thema|AND|dib AND palette|Themen, die "dib" und "Palette" enthalten.|  
|Einem der beiden Begriffe in einem Thema|OR|Raster OR Vektor|Themen, die entweder "Raster" oder "Vektor" enthalten.|  
|Nach dem ersten Begriff ohne den zweiten Begriff im gleichen Thema|NOT|"Betriebssystem" NOT DOS|Themen, die "Betriebssystem", jedoch nicht "DOS" enthalten.|  
|Beide Bedingungen, nahe beieinander in einem Thema|NEAR|Benutzer NEAR Kernel|Themen, die "Benutzer" in unmittelbarer Umgebung von "Kernel" enthalten.|  
  
## Siehe auch  
 [Tipps zur Volltextsuche](../ide/full-text-search-tips.md)   
 [Suchen nach Informationen](../ide/locate-information.md)