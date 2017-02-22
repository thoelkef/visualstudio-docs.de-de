---
title: "Datenquellen-Steuerarchitektur VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Verwaltungspaketen, Architektur"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Datenquellen-Steuerarchitektur VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Paket ist ein VSPackage Quellcodeverwaltung, das Dienste verwendet, die das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bereitstellt.  Bei der Ermittlung Quellcodeverwaltung stellt ein Paket für Quellcodeverwaltung als seine Funktionalität bereit.  Darüber hinaus kann ein Paket eine vielseitigere Quellcodeverwaltung als Alternative für ein Quellcodeverwaltungs\-Plug\-In Integrieren quellcodeverwaltung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Ein Quellcodeverwaltungs\-Plug\-In, das das Quellcodeverwaltungs\-Plug\-In API implementiert, wirft die einen strengen Vertrag unter.  Beispielsweise kann ein Plug\-In die standardmäßige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche nicht ersetzen.  Darüber hinaus kann das Quellcodeverwaltungs\-Plug\-In API kein Plug\-In, um ein eigenes Modell für die Quellcodeverwaltung zu implementieren.  Ein Paket überwindt Quellcodeverwaltung unterliegen jedoch beide Einschränkungen.  Ein Quellcodeverwaltung Paket verfügt über vollständige Kontrolle über die Quellcodeverwaltung Darstellung eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzers.  Außerdem kann ein Paket Quellcodeverwaltung Quellcodeverwaltung ein eigenes Modell und die Logik verwenden, und es kann die Quelle Steuerelement\-verknüpften Benutzeroberflächen definieren.  
  
## Quellcodeverwaltungs\-Paket\-Komponenten  
 Wie im Diagramm dargestellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Architektur ist eine Komponente, die den Namen Quellcodeverwaltungs\-Stub VSPackages, der Quellcodeverwaltung ein Paket mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert.  
  
 Quellcodeverwaltungs\-Stub behandelt die folgenden Aufgaben.  
  
-   Stellt das einheitliche Benutzeroberfläche bereit, das für die Registrierung der Quellcodeverwaltung Paket erforderlich ist.  
  
-   Lädt ein Paket Quellcodeverwaltung.  
  
-   Legt ein Paket Quellcodeverwaltung als aktiv oder inaktiv fest.  
  
 Quellcodeverwaltungs\-Stub durchsucht den aktuellen Dienst für das Paket Quellcodeverwaltung und leitet alle eingehenden Dienstaufrufe über die IDE in diesem Paket weiter.  
  
 Das Quellcodeverwaltungs\-Adapter\-Paket ist ein Paket, das die Quellcodeverwaltung besondere der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereitstellt.  Dieses Paket ist die zentrale Komponente zum Sichern von steckverbindungen Quellcodeverwaltung auf das Quellcodeverwaltungs\-Plug\-In API.  Wenn ein Quellcodeverwaltungs\-Plug\-In das aktive Plug\-In ist, sendet der Quellcodeverwaltungs\-Stub seine Ereignisse zum Quellcodeverwaltungs\-Adapter\-Paket.  Im Gegenzug ist das Quellcodeverwaltungs\-Adapter\-Paket das Quellcodeverwaltungs\-Plug\-In, indem Sie das Quellcodeverwaltungs\-Plug\-In APIs und stellt auch eine standardmäßige Benutzeroberfläche der Quellcodeverwaltung für alle steckverbindungen gemeinsam sind.  
  
 Wenn ein Paket Quellcodeverwaltung das aktuelle Paket ist hingegen ist der Quellcodeverwaltungs\-Stub das Paket direkt verbundenen, indem er die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Quellcodeverwaltungs\-Paket Schnittstellen verwendet.  Quellcodeverwaltung Das Paket ist für das Hosten einer eigenen Quellcodeverwaltung Benutzeroberfläche zuständig.  
  
 ![Grafik zur Quellcodeverwaltungs&#45;Architektur](../../extensibility/internals/media/vsipsccarch.png "VSIPSCCArch")  
  
 Für ein Paket Quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Code für die Quellcodeverwaltung nicht vorhanden oder eine API für die Integration an.  Vergleichen Sie dies mit dem Ansatz, der in [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md) gezeichnet wird, in dem das Quellcodeverwaltungs\-Plug\-In steifen einen Satz von Funktionen und Rückrufe implementieren muss.  
  
 Wie jedes VSPackage ist ein Paket Quellcodeverwaltung ein COM\-Objekt, das erstellt werden kann, indem `CoCreateInstance`verwendet.  VSPackage macht sich das zur Verfügung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>implementiert.  Wenn eine Instanz erstellt wurde, empfängt ein VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Website einen Zeiger und eine Schnittstelle, die den VSPackage\-Zugang zu den verfügbaren Dienste und Schnittstellen in der IDE bietet.  
  
 Das Schreiben eines VSPackage\-basierten erforderlich pakets Quellcodeverwaltung erweiterte Kenntnisse Programming API\-basiertes Plug\-In als ein Quellcodeverwaltungs\-Plug\-In schreiben.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)