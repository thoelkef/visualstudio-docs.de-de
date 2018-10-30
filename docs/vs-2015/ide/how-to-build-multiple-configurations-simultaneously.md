---
title: 'Vorgehensweise: Gleichzeitiges Erstellen mehrerer Konfigurationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa16c4c02f92f71d3288896d56b94a6d570c7dd4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930413"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Gewusst wie: Erstellen mehrerer Konfigurationen gleichzeitig
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Über das Dialogfeld **Batch erstellen** können Sie die meisten Projekttypen mit mehreren oder allen Buildkonfigurationen gleichzeitig erstellen. Die folgenden Projekttypen können Sie jedoch nicht gleichzeitig in mehreren Buildkonfigurationen erstellen:  
  
1. Für Windows erstellte [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]-Apps mit JavaScript.  
  
2. Für Visual Basic-Projekte.  
  
   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Erstellen eines Projekts in mehreren Buildkonfigurationen  
  
1.  Klicken Sie in der Menüleiste auf **Erstellen** > **Batch erstellen**.  
  
2.  Aktivieren Sie in der Spalte **Erstellen** die Kontrollkästchen für die Konfigurationen, in denen Sie ein Projekt erstellen möchten.  
  
    > [!TIP]
    >  Klicken Sie zum Bearbeiten oder Erstellen einer Konfiguration für eine Projektmappe in der Menüleiste auf **Erstellen** > **Konfigurations-Manager**, um das Dialogfeld **Konfigurations-Manager** zu öffnen. Nachdem Sie eine Buildkonfiguration für eine Projektmappe bearbeitet haben, klicken Sie im Dialogfeld **Batch erstellen** auf die Schaltfläche **Neu erstellen**, um alle Buildkonfigurationen für die Projekte in der Projektmappe zu aktualisieren.  
  
3.  Klicken Sie auf **Erstellen** oder **Neu erstellen**, um das Projekt mit den von Ihnen angegebenen Konfigurationen zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



