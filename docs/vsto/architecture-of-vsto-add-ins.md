---
title: "Architektur von VSTO-Add-Ins | Microsoft Docs"
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
  - "VSTOLoader.dll"
  - "Architektur [Office-Entwicklung in Visual Studio], Add-Ins auf Anwendungsebene"
  - "vstoee.dll"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Architektur"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Architektur"
ms.assetid: 978f102f-15c6-44e4-84e8-80b161408324
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 66
---
# Architektur von VSTO-Add-Ins
  VSTO\-Add\-Ins, die mit den Office Developer Tools in Visual Studio erstellt werden, verfügen über Architekturfunktionen, mit denen die Stabilität und Sicherheit gestärkt werden und die enge Zusammenarbeit mit Microsoft Office ermöglicht wird. In diesem Thema werden die folgenden Aspekte von VSTO\-Add\-Ins beschrieben:  
  
-   [Grundlegendes zu VSTO\-Add\-Ins](#UnderstandingAddIns)  
  
-   [Komponenten von VSTO\-Add\-Ins](#AddinComponents)  
  
-   [Verwenden von VSTO\-Add\-Ins mit Microsoft Office\-Anwendungen](#HowAddinsWork)  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Allgemeine Informationen zum Erstellen von VSTO\-Add\-Ins finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> Grundlegendes zu VSTO\-Add\-Ins  
 Wenn Sie die Office Developer Tools in Visual Studio verwenden, um ein VSTO\-Add\-In zu erstellen, erstellen Sie eine verwaltete Codeassembly, die von einer Microsoft Office\-Anwendung geladen wird. Nach dem Laden der Assembly kann das VSTO\-Add\-In auf Ereignisse reagieren, die in der Anwendung ausgelöst werden \(z. B. wenn ein Benutzer auf ein Menüelement klickt\). Außerdem kann das VSTO\-Add\-In einen Aufruf an das Objektmodell ausführen, um die Anwendung zu automatisieren und zu erweitern, und der Code kann alle Klassen in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] verwenden.  
  
 Die Assembly verwendet die primäre Interopassembly der Anwendung, um mit den COM\-Komponenten der Anwendung zu kommunizieren. Weitere Informationen finden Sie unter [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md) und [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Wenn für eine Anwendung mehrere VSTO\-Add\-Ins installiert werden, wird jedes VSTO\-Add\-In in einer anderen Anwendungsdomäne geladen. So kann ein VSTO\-Add\-In, das sich falsch verhält, nicht bewirken, dass für andere VSTO\-Add\-Ins Fehler auftreten. Es wird auch sichergestellt, dass beim Schließen der Anwendung alle VSTO\-Add\-In\-Assemblys aus dem Speicher entladen werden. Weitere Informationen zu Anwendungsdomänen finden Sie unter [Anwendungsdomänen](../Topic/Application%20Domains.md).  
  
> [!NOTE]  
>  VSTO\-Add\-Ins, die mit den Office Developer Tools in Visual Studio erstellt werden, sollen nur dann verwendet werden, wenn die Microsoft Office\-Hostanwendung von einem Endbenutzer gestartet wird. Wird die Anwendung programmgesteuert gestartet \(beispielsweise per Automatisierung\), verhält sich das VSTO\-Add\-In unter Umständen nicht wie erwartet.  
  
##  <a name="AddinComponents"></a> Komponenten von VSTO\-Add\-Ins  
 Die VSTO\-Add\-In\-Assembly ist zwar die Hauptkomponente, aber es gibt noch mehrere andere Komponenten, die eine wichtige Rolle dabei spielen, wie Microsoft Office\-Anwendungen VSTO\-Add\-Ins ermitteln und laden.  
  
### Registrierungseinträge  
 Microsoft Office\-Anwendungen ermitteln VSTO\-Add\-Ins, indem sie nach einem Satz von Registrierungseinträgen suchen. Eine vollständige Liste der von VSTO\-Add\-Ins verwendeten Registrierungseinträge finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Wenn Sie die Projektmappe erstellen, erstellt Visual Studio alle erforderlichen Registrierungseinträge auf dem Entwicklungscomputer, damit Sie Ihr VSTO\-Add\-In debuggen und ausführen können. Weitere Informationen finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
 Wenn Sie ClickOnce zum Bereitstellen Ihrer Lösung verwenden, erstellt das Setupprogramm, das während des Veröffentlichungsprozesses generiert wurde, auf dem Endbenutzercomputer automatisch die Registrierungsschlüssel. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### Bereitstellungsmanifest und Anwendungsmanifest  
 VSTO\-Add\-Ins verwenden Bereitstellungs\- und Anwendungsmanifeste, um die aktuelle Version der VSTO\-Add\-In\-Assembly zu identifizieren und zu laden. Das Bereitstellungsmanifest verweist auf das aktuelle Anwendungsmanifest. Das Anwendungsmanifest verweist auf die VSTO\-Add\-In\-Assembly und gibt die Einstiegspunktklasse an, die in der Assembly ausgeführt wird. Weitere Informationen finden Sie unter [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### Visual Studio Tools for Office Runtime  
 Zum Ausführen von mit den Office Developer Tools in Visual Studio erstellten VSTO\-Add\-Ins muss auf den Endbenutzercomputern [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installiert sein. Die Laufzeit enthält nicht verwaltete Komponenten und einen Satz verwalteter Assemblys. Die nicht verwalteten Komponenten laden die VSTO\-Add\-In\-Assembly. Die verwalteten Assemblys enthalten das Objektmodell, das Ihr VSTO\-Add\-In\-Code verwendet, um die Hostanwendung zu automatisieren und zu erweitern.  
  
 Weitere Informationen finden Sie unter [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> Verwenden von VSTO\-Add\-Ins mit Microsoft Office\-Anwendungen  
 Wenn ein Benutzer eine Microsoft Office\-Anwendung startet, verwendet die Anwendung das Bereitstellungsmanifest und das Anwendungsmanifest, um die aktuelle Version der VSTO\-Add\-In\-Assembly zu suchen und zu laden. Die folgende Abbildung zeigt die grundlegende Architektur dieser VSTO\-Add\-Ins.  
  
 ![Office 2007-Add-In-Architektur](../vsto/media/office07addin.png "Office 2007-Add-In-Architektur")  
  
> [!NOTE]  
>  In Office\-Projektmappen, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] abzielen, rufen Projektmappen das Objektmodell der Hostanwendung mithilfe von in die Projektmappenassembly eingebetteten PIA\-Typinformationen auf, statt die PIA direkt aufzurufen. Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md).  
  
### Ladevorgang  
 Die folgenden Schritte werden ausgeführt, wenn ein Benutzer eine Anwendung startet:  
  
1.  Die Anwendung überprüft die Registrierung auf Einträge, mit denen VSTO\-Add\-Ins identifiziert werden, die mit den Office Developer Tools in Visual Studio erstellt wurden.  
  
2.  Wenn die Anwendung diese Registrierungseinträge findet, lädt die Anwendung die Datei „VSTOEE.dll“, mit der wiederum die Datei „VSTOLoader.dll“ geladen wird. Hierbei handelt es sich um nicht verwaltete DLLs, die die Ladeprogrammkomponenten für Visual Studio 2010\-Tools für Office\-Laufzeit sind. Weitere Informationen finden Sie unter [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll lädt [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] und startet den verwalteten Teil von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] führt eine Prüfung auf Manifestaktualisierungen durch und lädt die aktuellen Anwendungs\- und Bereitstellungsmanifeste herunter.  
  
5.  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] führt eine Reihe von Sicherheitsüberprüfungen durch. Weitere Informationen finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
6.  Wenn das VSTO\-Add\-In vertrauenswürdig ist und ausgeführt werden darf, verwendet [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] das Bereitstellungsmanifest und das Anwendungsmanifest, um nach Assemblyaktualisierungen zu suchen. Wenn eine neue Version der Assembly verfügbar ist, lädt die Laufzeit die neue Version der Assembly in den [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Cache auf dem Clientcomputer. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
7.  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] erstellt eine neue Anwendungsdomäne, in die die VSTO\-Add\-In\-Assembly geladen wird.  
  
8.  Die VSTO\-Add\-In\-Assembly wird von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] in die Anwendungsdomäne geladen.  
  
9. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>\-Methode in Ihrem VSTO\-Add\-In auf, wenn Sie sie außer Kraft gesetzt haben.  
  
     Sie können diese Methode optional außer Kraft setzen, um in Ihrem VSTO\-Add\-In ein Objekt für andere Microsoft Office\-Projektmappen verfügbar zu machen. Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft die <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>\-Methode in Ihrem VSTO\-Add\-In auf, wenn Sie sie außer Kraft gesetzt haben.  
  
     Sie können diese Methode optional außer Kraft setzen, um eine Microsoft Office\-Funktion zu erweitern, indem Sie ein Objekt zurückgeben, mit dem eine Erweiterbarkeitsschnittstelle implementiert wird. Weitere Informationen finden Sie unter [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] führt separate Aufrufe der <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>\-Methode für die einzelnen Erweiterbarkeitsschnittstellen durch, die von der Hostanwendung unterstützt werden. Obwohl der erste Aufruf der <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>\-Methode normalerweise vor dem Aufruf der `ThisAddIn_Startup`\-Methode erfolgt, sollten in Ihrem VSTO\-Add\-In keine Annahmen dazu getroffen werden, wann oder wie oft die <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>\-Methode aufgerufen wird.  
  
11. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft die `ThisAddIn_Startup`\-Methode in Ihrem VSTO\-Add\-In auf. Diese Methode ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Startup>\-Ereignis. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
## Siehe auch  
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)   
 [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  