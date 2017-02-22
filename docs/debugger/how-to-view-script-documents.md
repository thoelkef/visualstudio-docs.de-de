---
title: "Gewusst wie: Anzeigen von Skriptdokumenten | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Skript-Explorer"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anzeigen von Skriptdokumenten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In früheren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Fenster Skript\-Explorer angezeigt.  Da das Fenster Skript\-Explorer häufig ausgeblendet war, war die Verfügbarkeit clientseitiger Skripts nicht immer direkt erkennbar.  
  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] werden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Projektmappen\-Explorer angezeigt, der standardmäßig immer eingeblendet ist.  Das Fenster Skript\-Explorer wurde entfernt.  
  
 Clientseitige Skriptdateien sind nur sichtbar, wenn Sie sich im Debugmodus oder Unterbrechungsmodus befinden.  Sie werden im Knoten **Skriptdokumente** angezeigt.  
  
 Serverseitige Skriptdateien sind immer sichtbar.  Sie werden im Knoten **\<Website\-Pfadname\>** angezeigt.  Der Name des Knotens ist mit diesem Beispiel vergleichbar: `c:\...\Website2\`  
  
### So zeigen Sie ein serverseitiges Skriptdokument an  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** den Knoten **\<Website\-Pfadname\>**.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die serverseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
### So zeigen Sie ein clientseitiges Skriptdokument an  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** den Knoten **Skriptdokumente**.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die clientseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
## Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)