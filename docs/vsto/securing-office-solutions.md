---
title: "Sichern von Office-Projektmappen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Sicherheit"
  - "Office-Entwicklung in Visual Studio, Sicherheit"
  - "Sicherheit [Office-Entwicklung in Visual Studio]"
ms.assetid: af840916-dda4-4e52-b536-802ebcab30ca
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 77
---
# Sichern von Office-Projektmappen
  Das Sicherheitsmodell für Office\-Projektmappen beinhaltet verschiedene Technologien: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], das Vertrauensstellungscenter in Microsoft Office und die Zone für eingeschränkte Sites in Internet Explorer. In den folgenden Abschnitten wird die Funktionsweise der verschiedenen Sicherheitsfunktionen beschrieben:  
  
-   [Gewähren von Vertrauenswürdigkeit für Office\-Projektmappen](#GrantingTrustToSolutions)  
  
-   [Gewähren von Vertrauenswürdigkeit für Dokumente](#GrantingTrustToDocuments)  
  
-   [Gewähren von Vertrauenswürdigkeit beim Verwenden von Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Überlegungen zur Sicherheit von Office\-Projektmappen](#Security)  
  
-   [Sicherheit während der Entwicklung](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools for Office Runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Gewähren von Vertrauenswürdigkeit für Office\-Projektmappen  
 Das Gewähren von Vertrauenswürdigkeit für Office\-Projektmappen bedeutet das Ändern der Sicherheitsrichtlinie jedes Endbenutzers, um der Office\-Lösung auf Grundlage der folgenden Beweise zu vertrauen:  
  
-   Das Zertifikat, das zum Signieren des Bereitstellungsmanifests verwendet wird.  
  
-   Die URL des Bereitstellungsmanifests.  
  
 Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Gewähren von Vertrauenswürdigkeit für Dokumente  
 Eine Anpassung auf Dokumentebene erfordert, dass sich das Dokument in einem Verzeichnis befindet, das als vertrauenswürdiger Speicherort festgelegt ist.  Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Gewähren von Vertrauenswürdigkeit beim Verwenden von Windows Installer  
 Sie können Windows Installer verwenden, um eine MSI\-Datei zum Installieren von Office\-Projektmappen in das Verzeichnis "Programme" zu erstellen, wofür Administratorrechte erforderlich sind.  Bei Office\-Projektmappen im Verzeichnis "Programme" sehen die Visual Studio 2010\-Tools für Office Runtime diese Office\-Projektmappen als vertrauenswürdig an und zeigen die ClickOnce\-Eingabeaufforderung für die Vertrauenswürdigkeit nicht an.  
  
##  <a name="Security"></a> Überlegungen zur Sicherheit von Office\-Projektmappen  
 Die Sicherheitsfeatures, die von [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] und Microsoft Office bereitgestellt werden, können zum Schutz vor verschiedenen Sicherheitsbedrohungen in Office\-Projektmappen beitragen.  Weitere Informationen finden Sie unter [Überlegungen zur Sicherheit von Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Sicherheit während der Entwicklung  
 Um Ihren Entwicklungsprozess zu vereinfachen, legt Visual Studio die Sicherheitsrichtlinie, die zum Ausführen und Debuggen der Projektmappe auf dem Computer benötigt wird, bei jedem Erstellen eines Projekts fest.  In einigen Szenarien müssen Sie möglicherweise zusätzliche Schritte zum Entwickeln des Projekts ausführen.  
  
### Projektmappen auf Dokumentebene  
 Wenn Sie die folgenden Typen von Projekten entwickeln, muss der vollqualifizierte Pfad eines Dokuments zur Liste der vertrauenswürdigen Speicherorte in der Microsoft Office\-Anwendung hinzugefügt werden:  
  
-   Projektmappen auf Dokumentebene, die sich auf einer Dateifreigabe im Netzwerk wie z. B. *\\\\Servername\\Freigabename* befinden.  
  
-   Projektmappen auf Anwendungsebene für Word, die DOC\- oder DOCM\-Dateien verwenden.  
  
 Schließen Sie die Unterverzeichnisse ein, wenn Sie den Dokumentspeicherort der Liste vertrauenswürdiger Speicherorte hinzufügen, oder schließen Sie insbesondere die Debug\- und Buildordner ein.  Weitere Informationen finden Sie im Microsoft Office Online\-Hilfeartikel [Erstellen, Entfernen oder Ändern eines vertrauenswürdigen Speicherorts für Ihre Dateien](https://support.office.com/de-de/article/Erstellen-Entfernen-oder-%C3%84ndern-eines-vertrauensw%C3%BCrdigen-Speicherorts-f%C3%BCr-Ihre-Dateien-f5151879-25ea-4998-80a5-4208b3540a62?ui=de-DE&rs=de-DE&ad=DE).  
  
### Temporäre Zertifikate  
 Visual Studio erstellt ein temporäres Zertifikat, wenn ein signierendes Zertifikat nicht bereits vorhanden ist.  Sie sollten dieses temporäre Zertifikat nur während der Entwicklung verwenden und ein offizielles Zertifikat für die Bereitstellung erwerben.  
  
 Das temporäre Zertifikat wird nach dem ersten Erstellen eines Office\-Projekts generiert.  Beim nächsten Drücken der Taste F5 wird das Projekt neu erstellt, da das Projekt als geändert markiert wird, wenn das Zertifikat hinzugefügt wird.  
  
 Nach einer Weile kann es zahlreiche temporäre Zertifikate geben, sodass Sie sie gelegentlich löschen sollten.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools for Office Runtime  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verfügt über Funktionen zur Überprüfung der Identität des Herausgebers und der Berechtigungen, die einer Anpassung gewährt werden.  Diese Berechtigungen werden mithilfe einer Reihe von Sicherheitsüberprüfungen verifiziert.  
  
### Sicherheit beim Laden der Anpassung  
 Beim Laden einer Anpassung auf Dokumentebene überprüft [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] immer, ob sich das Dokument in der Liste der vertrauenswürdigen Speicherorte befindet.  Außerdem überprüft die Laufzeit, ob die Projektmappe im Anwendungsmanifest FullTrust anfordert. Beim Laden der Anpassung werden keine zusätzlichen Sicherheitsüberprüfungen durchgeführt.  
  
### Abfolge der Sicherheitsüberprüfungen während der Installation  
 Wenn eine Office\-Projektmappe installiert oder aktualisiert wird, führt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] eine Reihe von Sicherheitsüberprüfungen in einer bestimmten Reihenfolge aus, um eine Entscheidung über die Vertrauenswürdigkeit zu treffen.  Eine Projektmappe wird nur dann installiert oder aktualisiert, wenn die Laufzeit bestimmt, dass die Projektmappe vertrauenswürdig ist.  
  
 Sie können den Installationsvorgang auf vier Arten starten: durch Ausführen des Setupprogramms, durch Öffnen des Bereitstellungsmanifests, durch Öffnen des Microsoft Office\-Anwendungshosts oder durch Ausführen von VSTOInstaller.exe.  
  
 Die erste Sicherheitsüberprüfung gilt nur für Projektmappen auf Dokumentebene.  Das Dokument einer Projektmappe auf Dokumentebene muss sich an einem vertrauenswürdigen Speicherort befinden.  Wenn sich das Dokument in einer Remotenetzwerk\-Dateifreigabe befindet oder eine Dateinamenerweiterung .doc oder .docm aufweist, muss der Speicherort des Dokuments der Liste vertrauenswürdiger Speicherorte hinzugefügt werden.  Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
 ![VSTO-Sicherheit – Installation aus Microsoft Office](../vsto/media/host-install.png "VSTO-Sicherheit – Installation aus Microsoft Office")  
  
 Die nächsten Sicherheitsüberprüfungen erfolgen durch [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und ClickOnce.  Um diese Überprüfungen zu bestehen, müssen Office\-Projektmappen FullTrust\-Berechtigungen anfordern, mit einem Zertifikat signiert werden, das nicht in der Liste der nicht vertrauenswürdigen Herausgeber aufgeführt ist, und sich an einem Speicherort befinden, der sich nicht in der eingeschränkten Zone von Internet Explorer befindet.  Wenn sich das Zertifikat in der Liste vertrauenswürdiger Herausgeber befindet, wird die Projektmappe sofort installiert.  Andernfalls fährt die Lösung mit der letzten letzte Gruppe von Überprüfungen fort, sofern keine der Überprüfungen fehlgeschlagen ist.  
  
 ![VSTO-Sicherheit für Installation von Lösungen](../vsto/media/installing.png "VSTO-Sicherheit für Installation von Lösungen")  
  
 Wenn die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung zulässig ist und der Projektmappe noch keine Vertrauenswürdigkeit gewährt wurde, gibt die Laufzeit dem Endbenutzer die Möglichkeit, die Entscheidung über die Vertrauenswürdigkeit zu treffen.  Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt, wird der Benutzeraufnahmeliste ein Eintrag hinzugefügt.  Alle Projektmappen in der Benutzeraufnahmeliste haben volle Vertrauenswürdigkeit und können installiert und ausgeführt werden.  
  
 Ab Visual Studio 2010 wird die Aufnahmeliste umgangen, wenn die Office\-Projektmappe mithilfe von Windows Installer \(MSI\) in das Verzeichnis "Programme" installiert wurde.  Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![VSTO-Sicherheit – Installation mit dem Setupprogramm](../vsto/media/setup-vstoinstaller.png "VSTO-Sicherheit – Installation mit dem Setupprogramm")  
  
## Siehe auch  
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Gewusst wie: Konfigurieren der Aufnahmelistensicherheit](../vsto/how-to-configure-inclusion-list-security.md)   
 [Gewusst wie: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Reference](../deployment/clickonce-reference.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  