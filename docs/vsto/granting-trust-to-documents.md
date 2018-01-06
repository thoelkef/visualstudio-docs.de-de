---
title: "Gewähren von Vertrauenswürdigkeit für Dokumente | Microsoft Docs"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 31fd8ba79218c6844e8fc5af33a81ce1c95a8abf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="granting-trust-to-documents"></a>Granting Trust to Documents
  Ein Projekt auf Dokumentebene verfügt über die gleichen Sicherheitsanforderungen wie Projekte auf Anwendungsebene: Signieren der Manifeste mit einem Zertifikat oder durch Klicken auf die vertrauenswürdige Eingabeaufforderung. Darüber hinaus muss sich das Dokument oder die Arbeitsmappe in einem Verzeichnis befinden, das als vertrauenswürdiger Speicherort festgelegt ist.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Vertrauenswürdige Speicherorte  
 Anwendungen in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Office 2010 über Trust Centers, in denen Benutzer Sicherheits- und Datenschutzinformationen Einstellungen, wie beispielsweise vertrauenswürdige Speicherorte konfigurieren können. Für Office-Projektmappen wird der lokale Computer als vertrauenswürdiger Speicherort betrachtet. Aufgrund des höheren Risikos gibt es bestimmte Verzeichnisse, die niemals als vertrauenswürdig eingestuft werden, z. B. die temporären Ordner für das System, für jeden Benutzer und für Internet Explorer.  
  
 Weitere Informationen über das Trust Center finden Sie unter [Sicherheitsrichtlinien und-Einstellungen unter Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Weitere Informationen zum Erstellen, verwalten, entfernen und Konfigurieren von vertrauenswürdigen Ordnern finden Sie unter [vertrauenswürdige Speicherorte und Einstellungen für vertrauenswürdige Herausgeber in 2007 Office System konfigurieren](http://go.microsoft.com/fwlink/?LinkId=89203) und [erstellen, entfernen oder Ändern einer vertrauenswürdigen Speicherort für Ihre Dateien](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Überlegungen zur Sicherheit von Office-Projektmappen  
 Es gibt mehrere Sicherheitsaspekte, wenn man überlegt, welche Ordner den vertrauenswürdigen Speicherorten hinzugefügt werden sollen:  
  
-   Lokale Ordner werden als sicherer und implizit vertrauenswürdig betrachtet. Remotespeicherorte, wie beispielsweise Dateifreigaben, müssen als vertrauenswürdige Speicherorte festgelegt werden.  
  
-   Wenn Sie den vertrauenswürdigen Speicherorten ein Verzeichnis hinzufügen, wird auf diese Weise nicht nur den Office-Projektmappen, sondern auch dem VBA- und ActiveX-Code die volle Vertrauenswürdigkeit gewährt. Aus diesem Grund dürfen das Stammverzeichnis und die Ordner "Eigene Dateien" nicht als vertrauenswürdig festgelegt werden.  
  
-   Obwohl das Dokument selbst durch die Verwendung der vertrauenswürdigen Speicherorte vertrauenswürdig ist, sind zusätzliche Berechtigungen erforderlich, damit die Anpassung als vertrauenswürdig eingestuft wird. Sie können der Anpassung volle Vertrauenswürdigkeit gewähren, indem Sie das Signieren der Manifeste mit einem Zertifikat verwenden, durch Klicken auf die vertrauenswürdige Eingabeaufforderung oder durch Installieren der Office-Projektmappe im Verzeichnis "Programme".  
  
-   Sie können das Dokument oder die Arbeitsmappe einer Projektmappe auf Dokumentebene im selben Verzeichnis wie die Assembly oder in einem anderen Verzeichnis speichern. Beispielsweise könnte sich das Dokument auf einem SharePoint-Server befinden, und die Assembly könnte auf einer Dateifreigabe im Netzwerk vorhanden sein. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer Office-Projektmappe auf Dokumentebene auf einem SharePoint-Server mithilfe von ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  