---
title: "Gewusst wie: Ausschlie&#223;en von Projekten aus einem Buildvorgang | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Gewusst wie: Ausschlie&#223;en von Projekten aus einem Buildvorgang
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Projektmappe erstellen, ohne dafür alle darin enthaltenen Projekte erstellen zu müssen.  Beispielsweise können Sie ein Projekt ausschließen, das die Erstellung unterbricht.  Sie können dann das Projekt erstellen, nachdem Sie die Probleme ermittelt und behoben haben.  
  
 Sie können ein Projekt wie folgt ausschließen:  
  
-   Entfernen Sie es temporär aus der aktiven Projektmappenkonfiguration.  
  
-   Durch das Erstellen einer Projektmappenkonfiguration, die das Projekt nicht enthält.  
  
 Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
### So entfernen Sie ein Projekt temporär aus der aktiven Projektmappenkonfiguration  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen** und dann **Konfigurations\-Manager** aus.  
  
2.  Suchen Sie in der Tabelle **Projektkontexte** nach dem aus dem Build auszuschließenden Projekt.  
  
3.  Deaktivieren Sie in der Spalte **Build** für das Projekt das Kontrollkästchen.  
  
4.  Wählen Sie die Schaltfläche **Schließen** aus, und erstellen Sie die Projektmappe dann erneut.  
  
### So erstellen Sie eine ein Projekt ausschließende Projektmappenkonfiguration  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen** und dann **Konfigurations\-Manager** aus.  
  
2.  Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **\<New\>** aus.  
  
3.  Geben Sie im Feld **Name** einen Namen für die Projektmappenkonfiguration ein.  
  
4.  Wählen Sie in der Liste **Einstellungen kopieren von** die Projektmappenkonfiguration aus, auf der die neue Konfiguration \(beispielsweise **Debug**\) basieren soll, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Deaktivieren Sie im Dialogfeld **Konfigurations\-Manager** das Kontrollkästchen in der Spalte **Erstellen** für das Projekt, das Sie ausschließen möchten, und wählen Sie dann die Schaltfläche **Schließen** aus.  
  
6.  Stellen Sie auf der Symbolleiste **Standard** sicher, dass es sich bei der neuen Projektmappenkonfiguration um die aktive Konfiguration im Feld **Projektmappenkonfigurationen** handelt.  
  
7.  Wählen Sie auf der Menüleiste **Erstellen** und dann **Projektmappe neu erstellen** aus.  
  
## Siehe auch  
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Gewusst wie: Erstellen mehrerer Konfigurationen gleichzeitig](../ide/how-to-build-multiple-configurations-simultaneously.md)