---
title: Verwenden von Office-Funktionen in Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1bcb827f068dd8c6577fed50e67d866ebba4886
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934621"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Verwenden von Office-Funktionen in Visual Studio
  Wenn Sie ein Projekt auf Dokumentebene erstellen, werden das Dokument und die zugehörige Anwendung innerhalb von Visual Studio gehostet, damit Sie entwerfen und direkt mit dem Dokument arbeiten können. Wenn Sie über ein Microsoft Office öffnen Sie die Anwendung in Visual Studio verfügen, werden in der Regel wie erwartet funktioniert. Allerdings einige der Funktionen der Anwendung ist anders oder nicht zugegriffen werden kann.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Dokumentschutz  
 Microsoft Office Word und Microsoft Office Excel bieten Schutzfunktionen, die Sie in Ihren Projekten verwenden können. Aber wenn Dokumentschutz aktiviert ist, während das Dokument in Visual Studio geöffnet ist, können Sie verhindern einige entwurfsänderungen. Weitere Informationen finden Sie unter [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Verwaltung von Informationsrechten  
 Information Rights Management (IRM) ist in Microsoft Office Word und Microsoft Office Excel verfügbar. IRM können Sie verhindern, dass nicht autorisierte Personen anzeigen oder Ändern von vertraulichen Informationen. Allerdings kann IRM auch Ihren Code Ausführung verhindern. Weitere Informationen finden Sie unter [Verwaltung von Informationsrechten und Erweiterungen für verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Kennwortschutz aufweisen  
 Microsoft Office Word-Dokumenten und Microsoft Office Excel-Arbeitsmappen können festgelegt werden, sodass sie von einer Person nicht geöffnet werden kann, die das Kennwort nicht bekannt ist. Kennwortschutz in Word und Excel anders behandelt, und Sie können Ihren Entwicklungsprozess beeinträchtigen. Weitere Informationen finden Sie unter [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Verwaltung von Informationsrechten und Erweiterungen für verwalteten code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Vorgehensweise: Öffnen Sie Office-Projektmappen ohne die Ausführung von code](../vsto/how-to-open-office-solutions-without-running-code.md)  
