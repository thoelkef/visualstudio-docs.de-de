---
title: "Dienste (Source Control VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, Source Control-Pakete"
  - "Source Control-Pakete, Dienste"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Dienste (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dienste sind der primäre Mechanismus, durch den Funktionen unter VSPackages und zwischen der integrierten Entwicklungsumgebung \(IDE\) von Visual Studio und den installierten VSPackages freigegeben wird.  Eine ausführliche Beschreibung von Diensten und ihrer Wichtigkeit in der Visual Studio\-IDE finden Sie unter[Verwendung und Bereitstellung von Diensten](../../extensibility/using-and-providing-services.md).  
  
## Der Quellcodeverwaltungs\-Dienst  
 Visual Studio stellt zwei Ebenen Dienste, IDE\-LEVEL\-Dienstleistungen und Dienste auf Paketebene.  Die IDE von Visual Studio stellt systemintern IDE\-LEVEL\-Dienstleistungen.  Das Paket Quellcodeverwaltung einige dieser Dienste in Anspruch nimmt.  Das Paket Quellcodeverwaltung als VSPackage gibt seine Funktionen für Quellcodeverwaltung frei, indem eine private dienstleistung Quellcodeverwaltung eigenen bereitstellt.  Das Paket Quellcodeverwaltung kapselt den Satz der Quelle Steuerelement\-verknüpften Schnittstellen, die von es in Form eines Vertrags implementiert werden, der von der Visual Studio\-IDE verwendet werden kann.  
  
## Siehe auch  
 [Design\-Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)