---
title: Source Control VSPackage-Architektur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a423b270eb8a26e9573f957da48915db37bf6851
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-vspackage-architecture"></a>Datenquellen-Steuerarchitektur VSPackage
Ein Paket für die quellcodeverwaltung ist eine VSPackage verwendet, die Dienste, von denen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bietet. Im Gegenzug stellt ein Datenquellen-Steuerelement Paket seine Funktionalität als einen quellcodeverwaltungsdienst bereit. Darüber hinaus ein Datenquellen-Steuerelement Paket ist ein flexibler Alternative als ein Quellcodeverwaltungs-Plug-In für die Integration der quellcodeverwaltung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Von einem strengen Vertrag hält sich in ein Quellcodeverwaltungs-Plug-in, das die Quelle Steuerelement-Plug-in-API implementiert. Beispielsweise ein plug-in kann nicht ersetzen Sie die standardmäßige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Benutzeroberfläche (UI). Darüber hinaus wird nicht die Datenquellen-Steuerelement-Plug-in-API für ein plug-in, das einen eigenen Steuerelement Quellmodell implementieren aktiviert. Ein Paket quellcodeverwaltung überwindet jedoch beide dieser Einschränkungen. Ein quellcodeverwaltung-Paket enthält die vollständige Kontrolle über die Quelle Steuerelement Erfahrungen aus einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer. Darüber hinaus eine quellcodeverwaltung Paket kann eigene Datenquellensteuerelement-Modell und die Logik, und es kann alle die Datenquellen-Steuerelement-bezogene Benutzeroberflächen definieren.  
  
## <a name="source-control-package-components"></a>Quellcodeverwaltung Paketkomponenten  
 Wie in der Architekturdiagramm dargestellt eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente, die mit dem Namen der Quelle Steuerelement Stub ist ein VSPackage, die ein Paket quellcodeverwaltung mit integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Source Control Stub behandelt die folgenden Aufgaben.  
  
-   Stellt die allgemeine Benutzeroberfläche, die für die quellcodeverwaltung für die Registrierung erforderlich ist.  
  
-   Lädt ein Paket für die quellcodeverwaltung.  
  
-   Ein Paket für die quellcodeverwaltung festgelegt als aktiv/inaktiv.  
  
 Source Control Stub für den Dienst aktiv für das Paket quellcodeverwaltung sucht und leitet alle eingehenden Dienstaufrufe aus der IDE für das Paket.  
  
 Das Quellcodeverwaltungspaket-Adapter ist ein spezieller Quellcodeverwaltungs-Paket, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereitstellt. Dieses Paket ist die zentrale Komponente für die Unterstützung von Source Control-Plug-ins basierend auf der Quelle Steuerelement-Plug-in-API. Wenn ein Quellcodeverwaltungs-Plug-in den aktiven-Plug-in ist, sendet Stub des Datenquellen-Steuerelement seine Ereignisse an das Quellcodeverwaltungspaket-Adapter. Wiederum das Quellcodeverwaltungspaket-Adapter kommuniziert mit dem Datenquellen-Steuerelement-Plug-in mithilfe der Datenquellen-Steuerelement-Plug-in-API und stellt auch eine Benutzeroberfläche, die für alle Datenquellen-Steuerelement-Plug-ins gemein sind.  
  
 Wenn ein Paket für die quellcodeverwaltung für die active-Paket ist, andererseits, Stub des Datenquellen-Steuerelement direkt kommuniziert mit dem Paket mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Quellcodeverwaltung Paket-Schnittstellen. Das Paket für die quellcodeverwaltung ist verantwortlich für das Hosten von eigenen quellcodeverwaltung UI.  
  
 ![Grafik zur quellverwaltungsarchitektur](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Für ein Paket quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcode-Steuerelement oder eine API für die Integration nicht bereitstellt. Vergleichen Sie dies mit dem Ansatz beschrieben, die in [erstellen eine Datenquellen-Steuerelement-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md) , in dem das Quellsteuerelement-Plug-in hat eine feste Gruppe von Funktionen und Rückrufe zu implementieren.  
  
 Wie alle VSPackage ist ein Paket für die quellcodeverwaltung ein COM-Objekt, das erstellt werden kann `CoCreateInstance`. Das VSPackage stellt selbst zur Verfügung, um die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Wenn eine Instanz erstellt wurde, erhält eine VSPackage einen Website-Zeiger und einer <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle, die die VSPackage-Zugriff auf die verfügbaren Dienste und Schnittstellen in der IDE bereitstellt.  
  
 Schreiben ein VSPackage-basierte quellcodeverwaltung Paket erfordert Erweiterte Programmierung Kenntnisse als das Schreiben einer Quelle Steuerelement-Plug-in-API-basierte-Plug-in.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)