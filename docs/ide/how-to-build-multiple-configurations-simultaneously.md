---
title: "Gewusst wie: Erstellen mehrerer Konfigurationen gleichzeitig | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Gewusst wie: Erstellen mehrerer Konfigurationen gleichzeitig
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die meisten Projekttypen können Sie mit mehreren oder allen Buildkonfigurationen gleichzeitig erstellen, indem Sie das Dialogfeld **Batch erstellen** verwenden.  Die folgenden Projekttypen können Sie jedoch nicht gleichzeitig in mehreren Buildkonfigurationen erstellen:  
  
1.  Für Windows erstellte [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-Apps mit JavaScript.  
  
2.  Für Visual Basic\-Projekte.  
  
 Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
### Erstellen eines Projekts in mehreren Buildkonfigurationen  
  
1.  Klicken Sie in der Menüleiste **Erstellen**, **Batch erstellen**.  
  
2.  Aktivieren Sie in der Spalte **Erstellen** die Kontrollkästchen für die Konfigurationen, in denen Sie ein Projekt erstellen möchten.  
  
    > [!TIP]
    >  Klicken Sie zum Bearbeiten oder Erstellen einer Konfiguration für eine Projektmappe in der Menüleiste auf **Erstellen**, **onfigurations\-Manager**, um das Dialogfeld **Konfigurations\-Manager** zu öffnen.  Nachdem Sie eine Buildkonfiguration für eine Projektmappe bearbeitet haben, klicken Sie im Dialogfeld **Batch erstellen** auf die Schaltfläche **Neu erstellen**, um alle Buildkonfigurationen für die Projekte in der Projektmappe zu aktualisieren.  
  
3.  Klicken Sie auf die Schaltfläche **Erstellen** oder **Neu erstellen**, um das Projekt mit den von Ihnen angegebenen Konfigurationen zu erstellen.  
  
## Siehe auch  
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)