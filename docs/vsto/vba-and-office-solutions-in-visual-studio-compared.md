---
title: VBA- und Office-Projektmappen in Visual Studio im Vergleich | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d6b2fd1cbf3ad2d58575b22b55f7ec1dc40b6ed4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Vergleich von VBA- und Office-Projektmappen in Visual Studio
  In Microsoft Visual Basic for Applications (VBA) wird nicht verwalteter Code verwendet, der eng in Office-Anwendungen integriert ist. Mit Microsoft Office-Projekten, die mit Visual Studio erstellt wurden, können Sie .NET Framework und Visual Studio-Entwurfstools nutzen.  
  
 Informationen zu den Typen von Office-Projektmappen können Sie mithilfe von Visual Studio erstellen, finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Vergleich  
 Die folgende Tabelle enthält einen grundlegenden Vergleich von VBA-Projektmappen und Office-Projektmappen in Visual Studio.  
  
|VBA-Projektmappen|Office-Projektmappen in Visual Studio|  
|-------------------|---------------------------------------|  
|Nutzt Code, der dauerhaft mit einem bestimmten Dokument verbunden ist.|Nutzt Code, der separat vom Dokument (für Anpassungen auf Dokumentebene) oder in einer Assembly gespeichert ist, die von der Anwendung geladen wird (für VSTO-Add-Ins).|  
|Funktioniert mit den Office-Objektmodellen und VBA-APIs.|Ermöglicht den Zugriff sowohl auf die Office-Objektmodelle als auch auf die [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] -APIs.|  
|Wurde für die Makroaufzeichnung und einen vereinfachten Entwicklungsprozess konzipiert.|Ist auf Sicherheit, einfachere Codewartung und die Möglichkeit ausgelegt, die vollständige integrierte Entwicklungsumgebung (IDE) von Visual Studio zu verwenden.|  
|Eignet sich gut für Projektmappen, die sehr eng in Office-Anwendungen integriert sind.|Eignet sich gut für Projektmappen, für die alle Ressourcen von Visual Studio und [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]genutzt werden.|  
|Verfügt über Einschränkungen für Unternehmen, insbesondere in den Bereichen Sicherheit und Bereitstellung.|Wurde für die Verwendung in Unternehmen konzipiert.|  
  
 Einige Dinge lassen sich mit VBA immer noch mit weniger Aufwand schneller erledigen. Es ist also ratsam, VBA weiterhin für Folgendes zu verwenden:  
  
-   Benutzerdefinierte Arbeitsblattfunktionen  
  
-   Aufzeichnen von Makros  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Kombinieren von VBA-Projektmappen und Office-Projektmappen, die mit Visual Studio erstellt wurden  
 Sie können VBA-Code aus Office-Projektmappen aufrufen, die mit Visual Studio erstellt wurden, und Sie können auch Code in Office-Projektmappen aus VBA aufrufen, die mit Visual Studio erstellt wurden. Das Verfahren richtet sich jeweils danach, ob es sich bei der Office-Projektmappe um ein VSTO-Add-In oder eine Anpassung auf Dokumentebene handelt. Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) und [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Kombinieren von VBA und Anpassungen auf Dokumentebene](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)   
 [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Erste Schritte &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  