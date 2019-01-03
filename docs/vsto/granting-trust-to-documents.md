---
title: Gewähren von Vertrauen für Dokumente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a60470d43842384103462fe69c4beba72bdc452d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912342"
---
# <a name="grant-trust-to-documents"></a>Gewähren von Vertrauen für Dokumente
  Ein Projekt auf Dokumentebene verfügt über die gleichen Sicherheitsanforderungen wie Projekte auf Anwendungsebene: Signieren der Manifeste mit einem Zertifikat oder durch Klicken auf die vertrauenswürdige Eingabeaufforderung. Darüber hinaus muss sich das Dokument oder die Arbeitsmappe in einem Verzeichnis befinden, das als vertrauenswürdiger Speicherort festgelegt ist.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Vertrauenswürdige Speicherorte  
 Anwendungen in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Office 2010 über Trust Centers, in dem Benutzer die Einstellungen für Sicherheit und Datenschutz, wie beispielsweise vertrauenswürdige Speicherorte konfigurieren können. Für Office-Projektmappen wird der lokale Computer als vertrauenswürdiger Speicherort betrachtet. Aufgrund des höheren Risikos gibt es bestimmte Verzeichnisse, die niemals als vertrauenswürdig eingestuft werden, z. B. die temporären Ordner für das System, für jeden Benutzer und für Internet Explorer.  
  
 Weitere Informationen über das Trust Center finden Sie unter [Sicherheitsrichtlinien und Einstellungen in Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Weitere Informationen über das Erstellen, verwalten, entfernen und Konfigurieren von vertrauenswürdigen Ordnern finden Sie unter [konfigurieren Sie vertrauenswürdige Speicherorte und Einstellungen für vertrauenswürdige Herausgeber in 2007 Office System](http://go.microsoft.com/fwlink/?LinkId=89203) und [erstellen, entfernen oder Ändern einer vertrauenswürdigen Speicherort für Ihre Dateien](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Überlegungen zur Sicherheit für Office-Projektmappen  
 Es gibt mehrere Sicherheitsaspekte, wenn man überlegt, welche Ordner den vertrauenswürdigen Speicherorten hinzugefügt werden sollen:  
  
-   Lokale Ordner werden als sicherer und implizit vertrauenswürdig betrachtet. Remotespeicherorte, wie beispielsweise Dateifreigaben, müssen als vertrauenswürdige Speicherorte festgelegt werden.  
  
-   Wenn Sie den vertrauenswürdigen Speicherorten ein Verzeichnis hinzufügen, wird auf diese Weise nicht nur den Office-Projektmappen, sondern auch dem VBA- und ActiveX-Code die volle Vertrauenswürdigkeit gewährt. Aus diesem Grund das Root-Verzeichnis und die *eigene* Ordner sollte nicht festgelegt werden als vertrauenswürdig.  
  
-   Obwohl das Dokument selbst durch die Verwendung der vertrauenswürdigen Speicherorte vertrauenswürdig ist, sind zusätzliche Berechtigungen erforderlich, damit die Anpassung als vertrauenswürdig eingestuft wird. Sie können die volle Vertrauenswürdigkeit für die Anpassung mithilfe von Signieren der Manifeste mit einem Zertifikat, klicken Sie auf die vertrauenswürdige Eingabeaufforderung oder installieren die Office-Projektmappe zu erteilen der *Programmdateien* Verzeichnis.  
  
-   Sie können das Dokument oder die Arbeitsmappe einer Projektmappe auf Dokumentebene im selben Verzeichnis wie die Assembly oder in einem anderen Verzeichnis speichern. Beispielsweise könnte sich das Dokument auf einem SharePoint-Server befinden, und die Assembly könnte auf einer Dateifreigabe im Netzwerk vorhanden sein. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer Office-Projektmappe auf Dokumentebene auf einem SharePoint Server mithilfe von ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewähren von Vertrauen für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Problembehandlung bei Office-projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
