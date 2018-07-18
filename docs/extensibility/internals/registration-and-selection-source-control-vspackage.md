---
title: Registrierung und Auswahl (Source Control VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d7bcdb8f930430ac00335777e2c088ce52a34bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133036"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrierung und Auswahl (Source Control VSPackage)
Ein Datenquellen-Steuerelement, das VSPackage registriert werden, um es zum Verfügbarmachen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Wenn mehrere Datenquellen-Steuerelements VSPackage registriert ist, kann der Benutzer die VSPackage, um zur richtigen Zeit jeweils Laden auswählen. Finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md) detaillierte Informationen zu VSPackages und zu registrieren.  
  
## <a name="registering-a-source-control-package"></a>Registrieren eine Steuerelement-Quellpaket  
 Das Quellcodeverwaltungspaket registriert ist, damit die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung finden sie und die Abfrage für die unterstützten Funktionen. Dies ist in Übereinstimmung mit einem verzögertes Laden-Schema, in dem eine Instanz eines Pakets erstellt wird, nur, wenn die Funktionen oder die Befehle erforderlich sind, oder explizit angefordert werden.  
  
 VSPackages platzieren Informationen in einem versionsspezifische Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X* ist die Hauptversionsnummer und *Y* ist die Nebenversionsnummer. Dieses Vorgehen ermöglicht den Zugriff auf die Seite-an-Seite Installation mehrerer Versionen unterstützen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Benutzeroberfläche (UI) unterstützt die Auswahl aus mehreren installierten Quelle Steuerelement-Plug-ins (über die Source Control Adapter-Paket) sowie quellcodeverwaltung VSPackages. Es kann nur eine aktive quellcodeverwaltung-Plug-in oder VSPackage zu einem Zeitpunkt. Kann jedoch wie unten beschrieben, die IDE Wechsel zwischen den Datenquellen-Steuerelement-Plug-ins und VSPackages über einen automatischen-basierten Lösung Austauschen von Paket Mechanismus. Es gibt einige Anforderungen seitens der quellcodeverwaltung VSPackage So aktivieren Sie diese Auswahlmechanismus.  
  
### <a name="registry-entries"></a>Registrierungseinträge  
 Ein Steuerelement Quellpaket benötigt drei private GUIDs:  
  
-   Paket-GUID: Dies ist die Haupt-GUID für das Paket, das Implementierung des Datenquellen-Steuerelements (in diesem Abschnitt als ID_Package bezeichnet) enthält.  
  
-   Datenquellen-Steuerelement-GUID: Dies ist eine GUID für die quellcodeverwaltung VSPackage verwendet, um mit der Visual Studio Quelle Steuerelement Stub registrieren und wird auch als ein Befehl Benutzeroberflächenkontext GUID verwendet. Die quellcodeverwaltungsdienst GUID ist die quellcodeverwaltung GUID registriert. Im Beispiel wird die GUID des Datenquellen-Steuerelements ID_SccProvider aufgerufen.  
  
-   Source Control-Dienst-GUID: Dies ist der private-Dienst-GUID, die von Visual Studio (in diesem Abschnitt als SID_SccPkgService bezeichnet) verwendet. Darüber hinaus muss das Quellcodeverwaltungspaket anderen GUIDs für VSPackages, Toolfenster, definieren und so weiter.  
  
 Die folgenden Registrierungseinträge müssen durch ein Datenquellen-Steuerelement VSPackage vorgenommen werden:  
  
|Schlüsselname|Einträge|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(Standard) = Rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(Standard) = Rg_sz:\<Anzeigename des Pakets ><br /><br /> Dienst = Rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(Standard) = Rg_sz: #\<Ressourcen-ID für lokalisierte Name ><br /><br /> Paket = Rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Beachten Sie, dass der Schlüsselname `SourceCodeControl`, wird bereits von verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und ist nicht als Option verfügbar \<PackageName >.)|(Standard) = Rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Wählen eine Steuerelement-Quellpaket  
 Mehrere Datenquellen-Steuerelement-Plug-in-API-basierte-Plug-ins und quellcodeverwaltung VSPackages gleichzeitig registriert werden können. Der Prozess der Auswahl einer Datenquellen-Steuerelement-Plug-in oder ein VSPackage muss sicherstellen, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt das plug-in oder zum entsprechenden Zeitpunkt VSPackage und können verzögern, Laden nicht benötigte Komponenten aus, bis sie benötigt werden. Darüber hinaus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] müssen alle UI aus anderen inaktiv VSPackages, einschließlich Menüelemente, Dialogfeldern und Symbolleisten, entfernen und Anzeigen der Benutzeroberfläche für das VSPackage aktiv.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein Datenquellen-Steuerelement VSPackage lädt, wenn eine der folgenden Vorgänge ausgeführt wird:  
  
-   Lösung wird geöffnet (wenn die Projektmappe unter quellcodeverwaltung ist).  
  
     Wenn eine Projektmappe oder ein Projekt in der quellcodeverwaltung geöffnet wird, führt dazu, dass die IDE das Quellsteuerelement VSPackage, der für die betreffende Projektmappe geladen werden festgelegt wurde.  
  
-   Die Befehle im Menü des Datenquellen-Steuerelements VSPackage ausgeführt werden.  
  
 Ein VSPackage Komponenten laden sollte nur dann, wenn tatsächlich werden geplanten benötigten Datenquellen-Steuerelement verwendet (andernfalls wird als verzögerte Laden).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Automatische Lösung-basierte VSPackage austauschen  
 Sie können manuell austauschen, Datenquellen-Steuerelements VSPackages über die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Optionen** im Dialogfeld unter die **Quellcodeverwaltung** Kategorie. Automatische-basierten Lösung Paket austauschen bedeutet, dass ein Quellpaket für das Steuerelement, die für eine bestimmte Projektmappe festgelegt wurde automatisch als aktiv festgelegt ist, wenn die Projektmappe geöffnet wird. Jedes Steuerelement Quellpaket sollten implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der Wechsel zwischen den beiden behandelt source Control-Plug-ins (implementieren die Datenquellen-Steuerelement-Plug-in-API) und quellcodeverwaltung VSPackages.  
  
 Das Quellcodeverwaltungspaket-Adapter wird verwendet, um auf alle Datenquellen-Steuerelement-Plug-in-API-basierte wechseln-Plug-in. Der Prozess der Adapter die intermediate Quellpaket-Steuerelement wechseln, und bestimmen die Datenquellen-Steuerelement-Plug-in muss festgelegt werden, um aktiv oder inaktiv für den Benutzer transparent ist. Das Adapter-Paket ist immer aktiv, wenn Datenquellen-Steuerelement-Plug-in aktiv ist. Wechseln zwischen zwei Datenquellen-Steuerelement-Plug-ins Beträge einfach laden und Entladen von Plug-in-DLL. Ein Datenquellen-Steuerelement VSPackage umschalten, umfasst jedoch die IDE das entsprechende VSPackage lädt interagieren.  
  
 Ein Datenquellen-Steuerelement VSPackage aufgerufen, wenn eine Projektmappe geöffnet ist und der Registrierungsschlüssel für das VSPackage in der Projektmappendatei wird. Wenn die Projektmappe geöffnet ist, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sucht nach den Registrierungswert "" und die entsprechenden quellcodeverwaltung VSPackage lädt. Alle Datenquellen-Steuerelements VSPackages müssen die oben beschriebenen Registrierungseinträge. Eine Lösung, die in der quellcodeverwaltung ist ist als ein bestimmtes Quellcodeverwaltungs VSPackage zugeordnet markiert. Quellcodeverwaltung VSPackages implementieren, müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> So aktivieren Sie die automatische Lösung-basierte VSPackage austauschen.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio-Benutzeroberfläche zu Paketauswahl und problemlos wechseln  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet eine Benutzeroberfläche für die quellcodeverwaltung VSPackage und Plug-in-Auswahl in der **Optionen** im Dialogfeld unter die **Quellcodeverwaltung** Kategorie. Es ermöglicht dem Benutzer die Auswahl der aktiven quellcodeverwaltung-Plug-in oder das VSPackage. Eine Dropdown-Liste enthält:  
  
-   Alle installierten Quellpakete-Steuerelement  
  
-   Alle installierten Source Control-Plug-ins  
  
-   Eine option "Keine", wodurch Quellcodeverwaltungssystem deaktiviert  
  
 Nur die Benutzeroberfläche für die Auswahl des Steuerelements aktiv Quelle wird angezeigt. Die VSPackage-Auswahl Blendet die Benutzeroberfläche für das vorherige VSPackage und zeigt die Benutzeroberfläche für das neue Projekt. Das VSPackage aktive wird auf einzelne Benutzer ausgewählt. Wenn ein Benutzer mehrere Kopien von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gleichzeitig öffnen, kann jeweils eine andere aktive VSPackage potenziell verwenden. Wenn mehrere Benutzer mit dem gleichen Computer angemeldet sind, kann jeder Benutzer über separate Instanzen von verfügen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] öffnen, jeweils mit einem anderen aktiven VSPackage. Wenn mehrere Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geschlossen sind, von einem Benutzer, die Datenquellen-Steuerelements VSPackage, das für die letzten geöffneten Projektmappe das Standardsteuerelement Quelle VSPackage aktiv auf Neustart festgelegt werden Offlinezeit aktiv war.  
  
 Im Gegensatz zu früheren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ein IDE-Neustart ist nicht mehr die einzige Möglichkeit, Datenquellen-Steuerelements VSPackages zu wechseln. VSPackage-Auswahl erfolgt automatisch. Wechseln Pakete erfordert Windows-Benutzer Berechtigungen (nicht-Administrator oder Poweruser).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funktionen](../../extensibility/internals/source-control-vspackage-features.md)   
 [Erstellen ein Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)