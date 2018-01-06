---
title: "Information Rights Management und Erweiterungen – Übersicht für verwalteten Code | Microsoft Docs"
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
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 21431cd16407d61db6f981aad68d52906c2de1f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Übersicht über Information Rights Management und Erweiterungen durch verwalteten Code
  Microsoft Office Word und Microsoft Office Excel bieten Information Rights Management (IRM), ein Feature, mit denen Sie verhindern, dass nicht autorisierte Benutzer nicht anzeigen oder ändern vertraulichen Informationen kann. Weitere Informationen zur Funktionsweise von Information Rights Management finden Sie Hilfe in der jeweiligen Anwendung.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Ausführen von Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen  
 Wenn die Projektmappe enthält ein Dokument oder eine Arbeitsmappe, die IRM standardmäßig verwendet, erlauben Word und Excel keine Ausführung von Code. Wenn Sie dem Autor des Dokuments sind oder über Vollzugriff verfügen, können Sie die Standardeinstellung ändern, sodass die Projektmappe funktioniert. Weitere Informationen finden Sie unter [Vorgehensweise: Zulassen von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 Verhindert die Verwendung von IRM <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> abrufen oder bearbeiten die im Dokument zwischengespeicherten Daten.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Endbenutzer können Einschränken von Berechtigungen für Dokumente, die Erweiterungen durch verwalteten Code verwenden.  
 Jeder Benutzer mit Vollzugriff auf das Dokument oder die Arbeitsmappe in der Projektmappe kann IRM verwenden, um Berechtigungen einzuschränken. Z. B. wenn ein Endbenutzer in der Buchhaltung eine Lösung, die ein Arbeitsblatt mit Daten aus einer Datenbank automatisch aufgefüllt verwendet, sollten dieser Benutzer Zugriff nur an Personen in sein eigenes Abteilung ändern und anderen Lesezugriff zulassen. Wenn der Benutzer die eingeschränkten Berechtigungen hinzufügt, wird standardmäßig der Code-behind das Arbeitsblatt kann nicht ausgeführt, und wird nicht im Arbeitsblatt mit Daten aufgefüllt.  
  
 Um das Problem zu beheben, muss ein Benutzer mit Vollzugriff auf das Dokument oder die Arbeitsmappe auf die Standardeinstellungen für die Berechtigung für den programmgesteuerten Zugriff auf das Objektmodell ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Zulassen von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  