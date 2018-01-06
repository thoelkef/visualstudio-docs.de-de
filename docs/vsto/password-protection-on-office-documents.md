---
title: "Kennwortschutz für Office-Dokumente | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f24c0493a66651a5d95925fd6777ba3e1cdd1658
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="password-protection-on-office-documents"></a>Kennwortschutz für Office-Dokumente
  Es ist möglich, ein Kennwort für Microsoft Office Word-Dokumente und Microsoft Office Excel-Arbeitsmappen festlegen, damit sie von einem Benutzer geöffnet werden können, die nicht das Kennwort kennt. Diese Option heißt auch **Kennwort beim Öffnen**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können Projekte auf Dokumentebene, die mithilfe vorhandener Dokumente und Arbeitsmappen mit erstellen **Kennwort beim Öffnen** aktiviert. Das Verhalten in Visual Studio unterscheidet sich für Word und Excel-Dokumenten, die über **Kennwort beim Öffnen** aktiviert.  
  
 Informationen zum Aktivieren der **Kennwort beim Öffnen**, finden Sie in Word oder Excel-Hilfe.  
  
## <a name="behavior-of-excel-and-word"></a>Das Verhalten von Excel und Word  
 Jedes Mal, wenn Sie eine Excel-Arbeitsmappe in Visual Studio öffnen, die hat **Kennwort beim Öffnen** aktiviert, Excel fordert Sie das Kennwort. Beim Erstellen der Projektmappe werden Sie für das Kennwort erneut aufgefordert werden, da das Dokument, während des Buildvorgangs geöffnet wird.  
  
 Beim ersten Öffnen Sie ein Word-Dokument in Visual Studio, ist **Kennwort beim Öffnen** aktiviert, Word fordert Sie das Kennwort. Nachdem Sie das Kennwort erfolgreich eingegeben **Kennwort beim Öffnen** aus dem Dokument entfernt wird und das Dokument zu öffnen, wird nicht mehr ein Kennwort erfordern. Wenn das Dokument in der Projektmappe verwendet werden soll, ein Kennwort erforderlich kann geöffnet ist, müssen Sie aktivieren **Kennwort beim Öffnen** nach dem letzten Build und vor dem Bereitstellen der Lösung.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management und Erweiterungen – Übersicht von verwaltetem Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Vorgehensweise: Zulassen von Code für die Ausführung Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  