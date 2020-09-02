---
title: Übersicht über das Automatisierungs Modell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699511"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungsmodell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Automatisierungs Modell besteht aus einem Satz von Objekten, für die Sie ein Visual Studio-Add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die die Visual Studio-Umgebung bearbeiten und häufige Aufgaben automatisieren kann. Mit einer Visual Studio-Erweiterung können benutzerdefinierte Visual Studio-Komponenten erstellt oder der Funktionalität von Standardkomponenten wie dem Text-Editor hinzugefügt werden.  
  
## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungs Modell  
 Das Automatisierungs Modell besteht aus verwandten Gruppen von Objekten, die die wichtigsten Facetten der allgemeinen Umgebung steuern. Im folgenden finden Sie ein Diagramm, das den umfangreichen Satz von Objekten anzeigt, die das Automatisierungs Modell bilden.  
  
 ![Diagramm des Visual Studio-Automatisierungsobjekts](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsvisualstudioautomationobjectchart")  
Visual Studio-Automatisierungs Objekte  
  
 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Die Umgebung stellt ein Modell für unterschiedliche Funktionsbereiche bereit. Beispielsweise gibt es ein Code Modell für verschiedene Elemente, die möglicherweise im Code gefunden werden. Es ist ein Dokument Modell für verschiedene Dokument Elemente vorhanden. Ein Bereich, der Projektbereich, ist von besonderem Interesse für VSPackage-Anbieter. Wahrscheinlich möchten Sie, dass Ihre neuen Projekttypen auf die gleiche Weise zum Automatisierungs Modell beitragen [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] zum Automatisierungs Modell beitragen. Dieser Vorgang ist unter [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)beschrieben.  
  
 Orte, an denen Sie in Erwägung gezogen werden, das Automatisierungs Modell der Umgebung zu erweitern:  
  
- Projekt  
  
- Dokument  
  
- Code  
  
- Entwickeln  
  
  Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Dieses Dokument und die Dokumente, zu denen es Links enthält, helfen Ihnen, Entscheidungen darüber zu treffen, wie Sie Automation für Ihr VSPackage bereitstellen sollten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Erstellen von Add-Ins](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
