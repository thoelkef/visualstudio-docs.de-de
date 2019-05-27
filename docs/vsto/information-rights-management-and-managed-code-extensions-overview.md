---
title: Verwaltung von Informationsrechten und Erweiterungen durch verwalteten code
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ca8f9d77681e3f11312e5e908a58ac2e292f581b
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177749"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Verwaltung von Informationsrechten und Erweiterungen für verwalteten code
  Microsoft Office Word und Microsoft Office Excel bieten Information Rights Management (IRM), ein Feature, mit denen Sie verhindern, dass nicht autorisierte Personen anzeigen oder Ändern von vertraulichen Informationen kann. Weitere Informationen zur Funktionsweise von Information Rights Management finden Sie Hilfe in der jeweiligen Anwendung.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Führen Sie die CodeBehind-Dokumenten mit eingeschränkten Berechtigungen
 Wenn die Projektmappe enthält ein Dokument oder eine Arbeitsmappe, die IRM, wird standardmäßig verwendet, erlauben Word und Excel keine Ausführung von Code. Wenn Sie der Autor des Dokuments oder über den Vollzugriff verfügen, können Sie die Standardeinstellung ändern, so, dass Ihre Lösung funktioniert. Weitere Informationen finden Sie unter [Vorgehensweise: Zuzulassen Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 Verhindert die Verwendung von IRM <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> abrufen oder Bearbeiten von Daten, die im Dokument zwischengespeichert werden.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Endbenutzer zum Einschränken von Berechtigungen für Dokumente, die Erweiterungen durch verwalteten Code verwenden.
 Jede Person mit Vollzugriff auf das Dokument oder die Arbeitsmappe in der Projektmappe kann IRM verwenden, um Berechtigungen zu beschränken. Z. B. wenn ein Endbenutzer in der buchhaltungsabteilung eine Lösung, die ein Arbeitsblatt mit Daten aus einer Datenbank automatisch gefüllt verwendet, möchten dieser Benutzer Zugriff nur für Personen in seine Abteilung ändern und Lesezugriff auf andere Benutzer zu ermöglichen. Wenn der Benutzer die eingeschränkten Berechtigungen hinzufügt, wird standardmäßig der Code hinter dem Arbeitsblatt kann nicht ausgeführt, und das Arbeitsblatt nicht mit Daten aufgefüllt.

 Um das Problem zu beheben, muss ein Benutzer mit Vollzugriff auf das Dokument oder die Arbeitsmappe auf die Standardeinstellungen für die Berechtigung zum ermöglichen den programmgesteuerten Zugriff auf das Objektmodell ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Zuzulassen Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Siehe auch
- [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md)
- [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
- [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)
