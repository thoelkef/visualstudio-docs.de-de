---
title: Kennwortschutz für Office-Dokumente
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02deaccdd615bae0c948d50abdd41758dc701704
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671834"
---
# <a name="password-protection-on-office-documents"></a>Kennwortschutz für Office-Dokumente
  Es ist möglich, zum Festlegen eines Kennworts auf Microsoft Office Word-Dokumente und Microsoft Office Excel-Arbeitsmappen, sodass sie von einer Person nicht geöffnet werden kann, die das Kennwort nicht bekannt ist. Diese Option heißt **Kennwort beim Öffnen**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können Projekte auf Dokumentebene, die mithilfe vorhandener Dokumente und Arbeitsmappen, erstellen **Kennwort beim Öffnen** aktiviert. Das Verhalten in Visual Studio unterscheidet sich für Word und Excel-Dokumenten, die **Kennwort beim Öffnen** aktiviert.  
  
 Weitere Informationen zum Aktivieren **Kennwort beim Öffnen**, finden Sie in Word oder Excel-Hilfe.  
  
## <a name="behavior-of-excel-and-word"></a>Verhalten von Excel und Word  
 Jedes Mal, wenn Sie eine Excel-Arbeitsmappe in Visual Studio öffnen, die **Kennwort beim Öffnen** aktiviert, Excel aufgefordert, das Kennwort einzugeben. Wenn Sie die Projektmappe erstellen werden Sie für das Kennwort in diesem Fall aufgefordert, da das Dokument, während des Buildvorgangs geöffnet wird.  
  
 Beim ersten Öffnen Sie ein Word-Dokument, in Visual Studio, die **Kennwort beim Öffnen** aktiviert, Word aufgefordert, das Kennwort einzugeben. Nachdem Sie das Kennwort eingegeben **Kennwort beim Öffnen** aus dem Dokument entfernt wird, und Öffnen des Dokuments wird ein Kennwort nicht mehr benötigen. Wenn Sie das Dokument in Ihrer Projektmappe möchten, benötigen ein Kennwort ein, bevor es geöffnet werden kann, müssen Sie aktivieren **Kennwort beim Öffnen** nach dem letzten Build und vor dem Bereitstellen der Lösung.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Verwaltung von Informationsrechten und Erweiterungen für verwalteten code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Gewusst wie: zuzulassen Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  