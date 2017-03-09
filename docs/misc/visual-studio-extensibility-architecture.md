---
title: "Architektur der Visual Studio-Erweiterbarkeit | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, Umgebungsmodell"
  - "Umgebungsmodell, Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Architektur der Visual Studio-Erweiterbarkeit
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) ist ein Framework zum Hosten von VSPackages und für freigegebene es Diensten ausgetauscht.  Ein Beispiel hierfür ist die Methode, die die IDE die Benutzeroberfläche implementiert.  Die IDE stellt das Containerfenster und die Symbolleisten und Menüs.  Sie stellt auch eine Infrastruktur der zahlreichen COM, die die Benutzeroberfläche programmierbar machen.  Das vollständige Befehlsnamen und \- Routing behandlungs\- Benutzer Schema gibt ein geöffnetes Framework, das den einfachen Zugriff auf vorhandene und installiert sätzen Befehle anbietet.  
  
## Erweiterbarkeits\-Architektur  
 Die folgende Abbildung zeigt die Architektur der Referenz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an.  Beachten Sie, dass das Konzept der Softwareanwendung nicht vorhanden ist.  Stattdessen die IDE\-Host aufgerufen, software\-komponenten VSPackages die Anwendungsfunktionalität bereitstellen.  Diese Funktionalität wird wiederum über die IDE als Diensten gemeinsam genutzt.  VSPackages\-Angebot die Dienste und andere VSPackages\-Verwendung.  Der Standardwert der IDE stellt auch viele Spektrum von Diensten, z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>an, die den Zugriff auf die IDE\-Fenster Funktionalität bereitstellen.  
  
 ![Grafik zur Umgebungsarchitektur](../extensibility/internals/media/environment.png "environment")  
Generalisierte Ansicht der Visual Studio\-Architektur  
  
 Beachten Sie, dass die Beziehung zwischen VSPackages und Dienste bidirektional ist.  Obwohl durch andere Dienste VSPackages\-Verwendungs anboten, sie können jedoch auch eigene ihre Dienste anbieten, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>\-Schnittstelle verwenden.  Diese dienstbasierte Architektur wuchs aus der Implementierung des Microsoft ActiveX\-Designer auschecken, in der ein Dienst eine Gruppe von verwandten Schnittstellen, die eine Aufgabe ausführen.  Von einer strengen COM\-Blickpunkt müssen alle Schnittstellen eines bestimmten Diensts in einer einzigen COM\-Klasse implementiert werden.  
  
 Der Standardwert der IDE bietet wichtige Dienste, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>und <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>an, die von VSPackages verwendet werden.  In der folgenden Tabelle werden einige dieser Dienste aufgeführt und beschrieben.  Weitere Informationen finden Sie unter [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md).  
  
|IDE\-Dienst|Beschreibung|  
|-----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE\-Dienstleistungen, die Grundfunktionen, VSPackages und die Registrierung arbeiten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Stellt einfaches Fenster und Benutzeroberfläche\-verknüpfte Funktionen in der IDE, z. B. die Fähigkeit, Tools und Dokumentfenster zu erstellen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Stellt grundlegende Projektmappe\-verknüpfte Funktionen, z. B. die Fähigkeit, Projekte aufzulisten, neue Projekte zu erstellen, und Bildschirm, ändert.|  
  
 Aufgrund ihrer festen Integration von der Interaktion von freigegebenen Diensten, sind die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE und VSPackages eng voneinander abhängig.  Allerdings trotz ihrer Interaktion schließende unterschiedliche haben sie verantwortlich.  
  
 Das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE ist für die folgenden Aufgaben verwendet werden:  
  
-   Wichtige Dienste für externe VSPackages bereitstellen.  
  
-   Bereitstellen eine programmierbare Schnittstelle, die die Teilnahme mit Standard\-Benutzeroberfläche\-Elementen aktiviert.  
  
-   Instanzen von VSPackages von Benutzeraktionen wie gefordert oder durch andere Dienste Anfordern von VSPackages erstellen.  
  
-   Dienste bereitstellen, die für die Kommunikation zwischen Koordination und VSPackages aktivieren.  
  
-   Projektmappen und die erforderlichen Dateien verwalten.  
  
-   Bereitstellung der Fenster Verwaltung.  
  
-   routing und der Befehlsleiste \- Befehls bereitstellen, z. B. Menüs, Symbolleisten und Kontextmenüs.  
  
-   Auswahl, Kontext und Währung koordinieren.  
  
 VSPackages sind für die folgenden Aufgaben verwendet werden:  
  
-   Bestimmte Initialisierung und Enderoutinen ausführen.  
  
-   Informationen zum Schreiben in die Registrierung, der die IDE verwendet, um das entsprechende VSPackages zu den entsprechenden Zeiten zu laden.  
  
-   bieten die Dienste, die für die Kommunikation mit anderen VSPackages erforderlich sind.  
  
-   Bereitstellen von Implementierungen für neue Projekttypen, Editoren und Designer.  
  
-   Bereitstellen von Erweiterungen für integrierte Benutzeroberflächenelemente, z Aufgabenelemente, Toolboxelemente und das Dialogfeld Optionen.  
  
## Siehe auch  
 [Visual Studio Shell](../extensibility/internals/visual-studio-shell.md)   
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)