---
title: Sichern von Office-Projektmappen | Microsoft Docs
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
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 271aad509d5ad2adb764b55f93fa65a8178424bd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="securing-office-solutions"></a>Sichern von Office-Projektmappen
  Das Sicherheitsmodell für Office-Projektmappen beinhaltet verschiedene Technologien: die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], das Vertrauensstellungscenter in Microsoft Office und die Internet Explorer-Zone eingeschränkter Sites. In den folgenden Abschnitten wird die Funktionsweise der verschiedenen Sicherheitsfunktionen beschrieben:  
  
-   [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](#GrantingTrustToSolutions)  
  
-   [Gewähren von Vertrauenswürdigkeit für Dokumente](#GrantingTrustToDocuments)  
  
-   [Gewähren von Vertrauenswürdigkeit beim Verwenden von Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Überlegungen zur Sicherheit von Office-Projektmappen](#Security)  
  
-   [Sicherheit während der Entwicklung](#SecurityDuringDeployment)  
  
-   [Visual Studio-Tools für Office-Laufzeit](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a>Gewähren von Vertrauenswürdigkeit für Office-Projektmappen  
 Das Gewähren von Vertrauenswürdigkeit für Office-Projektmappen bedeutet das Ändern der Sicherheitsrichtlinie jedes Endbenutzers, um der Office-Lösung auf Grundlage der folgenden Beweise zu vertrauen:  
  
-   Das Zertifikat, das zum Signieren des Bereitstellungsmanifests verwendet wird.  
  
-   Die URL des Bereitstellungsmanifests.  
  
 Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a>Gewähren von Vertrauenswürdigkeit für Dokumente  
 Eine Anpassung auf Dokumentebene erfordert, dass sich das Dokument in einem Verzeichnis befindet, das als vertrauenswürdiger Speicherort festgelegt ist. Weitere Informationen finden Sie unter [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a>Gewähren von Vertrauenswürdigkeit beim Verwenden von Windows Installer  
 Sie können Windows Installer verwenden, um eine MSI-Datei zum Installieren von Office-Projektmappen in das Verzeichnis "Programme" zu erstellen, wofür Administratorrechte erforderlich sind. Für Office-Projektmappen in das Verzeichnis für Programmdateien Visual Studio 2010-Tools für Office-Laufzeit betrachtet diese Office-Projektmappen, vertrauenswürdig sind und nicht die ClickOnce-vertrauensaufforderung.  
  
##  <a name="Security"></a>Besondere Sicherheitsüberlegungen für Office-Projektmappen  
 Die Sicherheitsfeatures, die von [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] und Microsoft Office bereitgestellt werden, können zum Schutz vor verschiedenen Sicherheitsbedrohungen in Office-Projektmappen beitragen. Weitere Informationen finden Sie unter [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a>Sicherheit während der Entwicklung  
 Um Ihren Entwicklungsprozess zu vereinfachen, legt Visual Studio die Sicherheitsrichtlinie, die zum Ausführen und Debuggen der Projektmappe auf dem Computer benötigt wird, bei jedem Erstellen eines Projekts fest. In einigen Szenarien müssen Sie möglicherweise zusätzliche Schritte zum Entwickeln des Projekts ausführen.  
  
### <a name="document-level-solutions"></a>Projektmappen auf Dokumentebene  
 Wenn Sie die folgenden Typen von Projekten entwickeln, muss der vollqualifizierte Pfad eines Dokuments zur Liste der vertrauenswürdigen Speicherorte in der Microsoft Office-Anwendung hinzugefügt werden:  
  
-   Die Lösungen auf einer Dateifreigabe im Netzwerk wie z. B. auf Dokumentebene  *\\\servername\sharename*.  
  
-   Projektmappen auf Anwendungsebene für Word, die DOC- oder DOCM-Dateien verwenden.  
  
 Schließen Sie die Unterverzeichnisse ein, wenn Sie den Dokumentspeicherort der Liste vertrauenswürdiger Speicherorte hinzufügen, oder schließen Sie insbesondere die Debug- und Buildordner ein. Weitere Informationen finden Sie in der Microsoft Office Online-Hilfeartikel [erstellen, entfernen oder Ändern eines vertrauenswürdigen Speicherorts für Ihre Dateien](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Temporäre Zertifikate  
 Visual Studio erstellt ein temporäres Zertifikat, wenn ein signierendes Zertifikat nicht bereits vorhanden ist. Sie sollten dieses temporäre Zertifikat nur während der Entwicklung verwenden und ein offizielles Zertifikat für die Bereitstellung erwerben.  
  
 Das temporäre Zertifikat wird nach dem ersten Erstellen eines Office-Projekts generiert. Beim nächsten Drücken der Taste F5 wird das Projekt neu erstellt, da das Projekt als geändert markiert wird, wenn das Zertifikat hinzugefügt wird.  
  
 Nach einer Weile kann es zahlreiche temporäre Zertifikate geben, sodass Sie sie gelegentlich löschen sollten.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a>Visual Studio-Tools für Office-Laufzeit  
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verfügt über Funktionen zur Überprüfung der Identität des Herausgebers und der Berechtigungen, die einer Anpassung gewährt werden. Diese Berechtigungen werden mithilfe einer Reihe von Sicherheitsüberprüfungen verifiziert.  
  
### <a name="security-during-customization-loading"></a>Sicherheit beim Laden der Anpassung  
 Beim Laden einer Anpassung auf Dokumentebene, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] immer überprüft, ob das Dokument in der Liste vertrauenswürdiger Speicherorte befindet. Außerdem überprüft die Common Language Runtime an, ob die Projektmappe im Anwendungsmanifest FullTrust anfordert. Beim Laden der Anpassung werden keine zusätzlichen Sicherheitsüberprüfungen durchgeführt.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Abfolge der Sicherheitsüberprüfungen während der Installation  
 Wenn eine Office-Projektmappe installiert oder aktualisiert wird, führt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] eine Reihe von Sicherheitsüberprüfungen in einer bestimmten Reihenfolge aus, um eine Entscheidung über die Vertrauenswürdigkeit zu treffen. Eine Projektmappe wird nur dann installiert oder aktualisiert, wenn die Laufzeit bestimmt, dass die Projektmappe vertrauenswürdig ist.  
  
 Sie können den Installationsvorgang auf vier Arten starten: durch Ausführen des Setupprogramms, durch Öffnen des Bereitstellungsmanifests, durch Öffnen des Microsoft Office-Anwendungshosts oder durch Ausführen von VSTOInstaller.exe.  
  
 Die erste Sicherheitsüberprüfung gilt nur für Projektmappen auf Dokumentebene. Das Dokument einer Projektmappe auf Dokumentebene muss sich an einem vertrauenswürdigen Speicherort befinden. Wenn sich das Dokument in einer Remotenetzwerk-Dateifreigabe befindet oder eine Dateierweiterung .doc oder .docm aufweist, muss der Speicherort des Dokuments der Liste vertrauenswürdiger Speicherorte hinzugefügt werden. Weitere Informationen finden Sie unter [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
 ![VSTO-Sicherheit – Installation aus Microsoft Office](../vsto/media/host-install.png "VSTO-Sicherheit – Installation aus Microsoft Office")  
  
 Die nächsten Sicherheitsüberprüfungen erfolgen durch [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und ClickOnce. Office-Projektmappen um diese Überprüfungen erfolgreich sind, müssen FullTrust-Berechtigungen anfordern, werden mit einem Zertifikat signiert, die nicht in der Liste nicht vertrauenswürdiger Herausgeber aufgeführt ist und werden an einem Speicherort, der nicht in der eingeschränkten Zone von Internet Explorer ist. Wenn das Zertifikat in der Liste vertrauenswürdiger Herausgeber befindet, wird die Projektmappe sofort installiert. Andernfalls fährt die Lösung mit der letzten letzte Gruppe von Überprüfungen fort, sofern keine der Überprüfungen fehlgeschlagen ist.  
  
 ![VSTO-Sicherheit für das Installieren von Lösungen](../vsto/media/installing.png "VSTO-Sicherheit für das Installieren von Lösungen")  
  
 Wenn die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Trust-Eingabeaufforderung zulässig ist und die Projektmappe nicht noch Vertrauenswürdigkeit gewährt wurde, die Common Language Runtime lässt die Entscheidung über die Vertrauenswürdigkeit vom Benutzer vorgenommen werden. Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt, wird der Benutzeraufnahmeliste ein Eintrag hinzugefügt. Alle Projektmappen in der Benutzeraufnahmeliste haben volle Vertrauenswürdigkeit und können installiert und ausgeführt werden.  
  
 Ab Visual Studio 2010 wird die Aufnahmeliste umgangen, wenn die Office-Projektmappe mithilfe von Windows Installer (MSI) in das Verzeichnis "Programme" installiert wurde. Weitere Informationen finden Sie unter [vertrauen Office-Projektmappen mithilfe von Benutzeraufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![VSTO-Sicherheit – verwenden das Setupprogramm zur Installation](../vsto/media/setup-vstoinstaller.png "VSTO-Sicherheit – verwenden das Setupprogramm zur Installation")  
  
## <a name="see-also"></a>Siehe auch  
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Gewähren von Vertrauenswürdigkeit Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Vorgehensweise: Konfigurieren der Aufnahmelistensicherheit](../vsto/how-to-configure-inclusion-list-security.md)   
 [Vorgehensweise: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Referenz](/visualstudio/deployment/clickonce-reference)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  