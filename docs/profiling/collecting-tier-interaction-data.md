---
title: "Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE | Microsoft Docs"
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
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "Profilerstellungstools,ADO.NET-Profilerstellung"
  - "Ebeneninteraktions-Profilerstellungsmethode"
  - "Profilerstellungstools,Ebeneninteraktionsmethode"
  - "ADO.NET-Leistungsprofilerstellung"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der Funktionen von Anwendungen mit mehreren Ebenen, die über ADO.NET\-Dienste mit Datenbanken kommunizieren, bereit.  Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.  
  
 **Visual Studio\-Editionen**  
  
 Profilerstellungsdaten für die Ebeneninteraktion können mit Visual Studio Ultimate, Visual Studio Premium oder Visual Studio Professional gesammelt werden.  Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in VS Ultimate und VS Premium angezeigt werden.  
  
 **Windows 8 und Windows Server 2012**  
  
 Um Ebeneninteraktionsdaten für Windows 8\-Desktop\-Apps und Windows Server 2012\-Apps zu erfassen, müssen Sie die Instrumentationsmethode verwenden.  Sie können Ebeneninteraktionsdaten nicht für Windows Store\-Apps sammeln.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  Sie können Ebeneninteraktionsdaten in alle Profilerstellungsmethoden einer anderen unterstützten Version von Windows einschließen.  
  
 **Leistungs\-Assistent**  
  
 Aufgrund eines Fehlers im Leistungs\-Assistenten müssen Sie die Option zur Erfassung von Ebeneninteraktionsdaten einer Profilerstellung im Leistungs\-Explorer hinzufügen.  Sie müssen das Projekt, die ausführbare Datei oder die Website außerdem dem Zielknoten des Leistungs\-Explorers hinzufügen.  
  
### So fügen Sie einer Profilerstellung Ebeneninteraktionsdaten mithilfe der Eigenschaftenseiten der Leistungssitzung hinzu  
  
1.  Wählen Sie im Leistungs\-Explorer im Kontextmenü **Eigenschaften** aus.  
  
2.  Wählen Sie die Seite **Ebeneninteraktionen** aus, und aktivieren Sie das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren**.  
  
3.  Wählen Sie im Leistungs\-Explorer den Knoten **Ziele** aus, und geben Sie das Projekt, die ausführbare Datei oder die Website an, für das\/die Sie ein Profil erstellen möchten.  
  
## Siehe auch  
 [Ansicht "Ebeneninteraktionen"](../profiling/tier-interactions-view.md)