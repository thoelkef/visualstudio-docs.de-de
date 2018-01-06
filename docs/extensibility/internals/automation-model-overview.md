---
title: "Übersicht über die Benutzeroberflächenautomatisierungs-Modell | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 208357343a3e77e29b1dc0a98b6159c5ac3f957e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="automation-model-overview"></a>Übersicht über die Benutzeroberflächenautomatisierungs-Modell
Das Automatisierungsmodell besteht aus einem Satz von Objekten, die für die Sie eine Visual Studio-add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die Visual Studio-Umgebung bearbeiten kann, und Automatisieren allgemeiner Aufgaben. Eine Visual Studio-Erweiterung kann erstellen benutzerdefinierte Komponenten für Visual Studio oder die Funktionalität des standard-Komponenten, z. B. den Texteditor hinzufügen.  
  
## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungsmodell  
 Das Automatisierungsmodell besteht aus verbundene Gruppen von Objekten, die wichtigsten Aspekte der allgemeinen Umgebung steuern. Im folgenden finden ein Diagramm mit den umfangreichen Satz von Objekten, die das Automatisierungsmodell verfassen.  
  
 ![Diagramm des Visual Studio-Automatisierung](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "VsVisualStudioAutomationObjectChart")  
Visual Studio-Automatisierungsobjekte  
  
 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Die Umgebung bietet ein Modell für die unterschiedlichen Funktionsbereichen an. Es ist z. B. ein Codemodell für verschiedene Elemente, die sich im Code befindet. Es ist ein Dokumentmodell für verschiedene Dokumentelementen. Ein Bereich, der Projektbereich ist von besonderem Interesse für VSPackage-Anbieter. Sollen die neuen Projekttypen, die im großen und ganzen genauso wie zum Automatisierungsmodell beitragen wahrscheinlich [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Automatisierungsmodell beitragen. Prozess umrandet [bereitstellen Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Orte, wo Sie in Betracht ziehen können Erweitern des Automatisierungsmodells der Umgebung:  
  
-   Projekt  
  
-   Dokument  
  
-   Code  
  
-   Build  
  
 Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Dieses Dokument und die Dokumente enthält es Links, um Ihnen dabei helfen, Entscheidungen zur Automatisierung für Ihr VSPackage bereitzustellen sollten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen einer Add-Ins](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)