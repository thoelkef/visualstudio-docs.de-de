---
title: "Übersicht über die Benutzeroberflächenautomatisierungs-Modell | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>Übersicht über die Benutzeroberflächenautomatisierungs-Modell
Das Automatisierungsmodell besteht aus einem Satz von Objekten, für die Sie ein Visual Studio-add-in oder eine Erweiterung schreiben können. Ist ein Add-in in einer Anwendung, die die Visual Studio-Umgebung verändern und Automatisierung allgemeiner Aufgaben kann. Visual Studio-Erweiterung kann erstellen benutzerdefinierte Komponenten von Visual Studio oder die Funktionalität des standard-Komponenten wie der Text-Editor hinzufügen.  
  
## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungsmodell  
 Das Automatisierungsmodell besteht aus verwandten Gruppen von Objekten, die wichtigsten Aspekte der allgemeinen Umgebung steuern. Im folgenden finden ein Diagramm mit den umfassenden Satz von Objekten, die die Benutzeroberflächenautomatisierungs-Modell zu erstellen.  
  
 ![Diagramm des Visual Studio-Automatisierungsobjekts](~/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio-Automatisierungsobjekte  
  
 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Die Umgebung bietet ein Modell für verschiedene Funktionsbereiche. Es ist z. B. ein Codemodell für verschiedene Elemente, die im Code auftreten. Es ist ein Dokumentmodell für verschiedene Dokumentelementen. Ein Bereich, der Projektbereich ist von besonderem Interesse für VSPackage-Anbieter. Sie werden wahrscheinlich die neuen Projekttypen werden in die gleiche Weise wie das Automatisierungsmodell mitwirken [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zu Automatisierungsmodell beitragen. Der in beschriebenen Prozess [bietet Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Bereiche, in denen Sie Erweitern des Automatisierungsmodells der Umgebung berücksichtigen können:  
  
-   Projekt  
  
-   Dokument  
  
-   Code  
  
-   Build  
  
 Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). In diesem Dokument und die Dokumente bietet es Links, um Ihnen zu Entscheidungen zur Automatisierung für das VSPackage Bereitstellen von sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Erstellen einer Add-Ins](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
