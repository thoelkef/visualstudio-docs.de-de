---
title: "Gewusst wie: Konfigurieren von Projekten f&#252;r mehrere Zielplattformen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Plattformen, Ändern der Zielplattformen"
  - "Projekte [Visual Studio], Plattformen für"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Gewusst wie: Konfigurieren von Projekten f&#252;r mehrere Zielplattformen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kann eine Projektmappe gleichzeitig für mehrere verschiedene CPU\-Zielarchitekturen oder Zielplattformen konfiguriert werden.  Die Eigenschaften, um diese **Konfigurations\-Manager** werden durch das Festlegen Dialogfeld zugegriffen.  
  
## Festlegen einer Zielplattform  
 Das Dialogfeld **Konfigurations\-Manager** ermöglicht es Ihnen, Konfigurationen und Plattformen auf Projektmappenebene und Projektebene zu erstellen und festzulegen.  Jeder Kombination aus Konfigurationen und Zielen auf Projektmappenebene kann eine eindeutige Gruppe von Eigenschaften zugewiesen werden. Auf diese Weise können Sie problemlos zwischen Konfigurationen wechseln, beispielsweise von einer Releasekonfiguration für eine [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]\-Zielplattform zu einer Releasekonfiguration für eine x86\-Zielplattform oder einer Debugkonfiguration, die für eine x86\-Plattform ausgelegt ist.  
  
#### So legen Sie für die Konfiguration eine andere Zielplattform fest  
  
1.  Klicken Sie im Menü **Erstellen** auf die Option **Konfigurations\-Manager**.  
  
2.  Wählen Sie im Feld **Aktive Projektmappenplattform** die für die Projektmappe gewünschte Plattform aus, oder klicken Sie auf **\<Neu\>**, um eine neue Plattform zu erstellen.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompiliert die Anwendung auf die Plattform an, die als aktive Plattform **Konfigurations\-Manager** im Dialogfeld festgelegt wird.  
  
## Entfernen einer Plattform  
 Wenn Sie eine Plattform nicht mehr benötigen, können Sie sie über das Dialogfeld Konfigurations\-Manager entfernen.  Dadurch werden alle Projektmappen\- und Projekteinstellungen entfernt, die für diese Kombination aus Konfiguration und Ziel konfiguriert wurden.  
  
#### So entfernen Sie eine Plattform  
  
1.  Klicken Sie im Menü **Erstellen** auf die Option **Konfigurations\-Manager**.  
  
2.  Wählen Sie im Feld **Aktive Projektmappenplattform** die Option **\<Bearbeiten\>**.  Das Dialogfeld **Projektmappenplattformen bearbeiten** wird angezeigt.  
  
3.  Klicken Sie auf die zu entfernende Plattform und dann auf **Entfernen**.  
  
## Konfigurieren einer Projektmappe für mehrere Zielplattformen  
 Da Sie die Einstellungen auf der Grundlage der Einstellungen für die jeweilige Kombination aus Konfiguration und Plattform ändern können, ist es möglich, eine Projektmappe einzurichten, die für mehr als eine Zielplattform ausgelegt ist.  
  
#### So legen Sie mehrere Plattformen als Ziel fest  
  
1.  Fügen Sie im **Konfigurations\-Manager** mindestens zwei Zielplattformen für die Projektmappe hinzu.  
  
2.  Wählen Sie die gewünschte Zielplattform aus der Liste **Aktive Projektmappenplattform** aus.  
  
3.  Erstellen Sie die Projektmappe.  
  
#### So erstellen Sie mehrere Projektmappenkonfigurationen gleichzeitig  
  
1.  Fügen Sie im **Konfigurations\-Manager** mindestens zwei Zielplattformen für die Projektmappe hinzu.  
  
2.  Verwenden Sie das Fenster **Batch erstellen**, um mehrere Projektmappenkonfigurationen gleichzeitig zu erstellen.  
  
 Sie können über eine Plattform auf Projektmappenebene verfügen, z. B. [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], während keines der in der Projektmappe enthaltenen Projekte für dieselbe Zielplattform konfiguriert ist.  Es ist auch möglich, dass in einer Projektmappe mehrere Projekte enthalten sind, die jeweils für unterschiedliche Zielplattformen konfiguriert sind.  In einem solchen Fall wird empfohlen, eine neue Konfiguration mit einem beschreibenden Namen zu erstellen, um Verwechslungen auszuschließen.  
  
## Siehe auch  
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)