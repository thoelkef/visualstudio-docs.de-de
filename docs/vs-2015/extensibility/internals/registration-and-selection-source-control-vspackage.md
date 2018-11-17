---
title: Registrierung und Auswahl (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 636e70357c23059a505d657af0078653de413976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764459"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrierung und Auswahl (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Datenquellen-Steuerelement, das VSPackage registriert werden, um sie verfügbar machen die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Wenn mehr als eine quellcodeverwaltung VSPackage registriert ist, kann der Benutzer, die VSPackages, laden Sie zur richtigen Zeit jeweils auswählen. Finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md) für Weitere Informationen zu VSPackages und wie Sie sie zu registrieren.  
  
## <a name="registering-a-source-control-package"></a>Registrieren ein Quellcode-Verwaltungspaket  
 Der Quellcode-Verwaltungspaket wird registriert, damit die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung finden sie und die Abfrage für die unterstützten Funktionen. Dies ist in Übereinstimmung mit einem verzögertes Laden-Schema, in dem eine Instanz eines Pakets erstellt wird, nur, wenn die Funktionen oder die Befehle erforderlich sind, oder explizit angefordert werden.  
  
 VSPackages speichern Informationen in eine bestimmte Version Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X* ist die Nummer der Hauptversion und *Y* ist die Nummer der Nebenversion. Diese Vorgehensweise bietet die Möglichkeit zur Unterstützung von Seite-an-Seite Installation mehrerer Versionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzeroberfläche (UI) unterstützt eine Auswahl aus mehreren installierten Quellcodeverwaltungs-Plug-ins (über den Adapter der Quellcodeverwaltungspaket) sowie quellcodeverwaltung VSPackages. Es kann nur eine aktive quellcodeverwaltung-Plug-in oder VSPackage zu einem Zeitpunkt. Allerdings ermöglicht das wie unten beschrieben, die IDE Wechseln zwischen Quellcodeverwaltungs-Plug-ins und VSPackages durch eine automatische informationsreiche lösungsbasierte Austauschen von Paket Methode. Es gibt einige Anforderungen seitens das Quellcodeverwaltungs-VSPackage, um diesen Auswahlmechanismus zu aktivieren.  
  
### <a name="registry-entries"></a>Registrierungseinträge  
 Ein Quellcodeverwaltungspaket erfordert drei private GUIDs:  
  
- Paket-GUID: Dies ist die Haupt-GUID für das Paket, das Implementierung des Datenquellen-Steuerelements (in diesem Abschnitt als ID_Package bezeichnet) enthält.  
  
- Datenquellen-Steuerelement-GUID: Dies ist eine GUID für das Quellcodeverwaltungs-VSPackage verwendet, um mit der Visual Studio Quellcode-Verwaltungsstub registrieren und wird auch als eine befehlsbenutzeroberflächenkontext GUID verwendet. Die Datenquellen-Steuerelement-GUID ist die quellcodeverwaltung GUID registriert. Im Beispiel wird die quellcodeverwaltung GUID ID_SccProvider aufgerufen.  
  
- Source-Control-Dienst-GUID: Dies ist der private-GUID, die von Visual Studio (in diesem Abschnitt als SID_SccPkgService bezeichnet) verwendet. Darüber hinaus muss das Quellcodeverwaltungspaket anderen GUIDs für VSPackages, Toolfenster, definieren und so weiter.  
  
  Die folgenden Registrierungseinträge müssen durch ein Quellcodeverwaltungs-VSPackage vorgenommen werden:  
  
|Schlüsselname|Einträge|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(Standard) = Rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(Standard) = Rg_sz:\<Anzeigename des Pakets ><br /><br /> Dienst = Rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(Standard) = Rg_sz: #\<Ressourcen-ID für lokalisierte Name ><br /><br /> Paket = Rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Beachten Sie, dass der Schlüsselname, `SourceCodeControl`, wird bereits von verwendet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und ist nicht als Option verfügbar \<Paketname >.)|(Standard) = Rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Ein Quellcodeverwaltungspaket auswählen  
 Mehrere Datenquellen-Steuerelement-Plug-in-API-basierte-Plug-ins und Datenquellen-Steuerelement, die VSPackages gleichzeitig registriert werden können. Der Prozess der Auswahl einer Datenquellen-Steuerelement-Plug-in oder VSPackage muss sicherstellen, dass [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lädt das plug-in oder VSPackage zum richtigen Zeitpunkt, und können nicht benötigte Komponenten geladen, bis sie benötigt werden. Darüber hinaus [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] muss, entfernen Sie alle Benutzeroberfläche aus anderen inaktiv VSPackages, einschließlich werden, Menüelemente, Dialogfelder und Symbolleisten, und zeigt die grafische Benutzeroberfläche für das VSPackage aktiv.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Lädt ein Quellcodeverwaltungs-VSPackage, wenn eine der folgenden Vorgänge ausgeführt wird:  
  
- Projektmappe wird geöffnet, (wenn die Projektmappe unter quellcodeverwaltung befindet).  
  
   Wenn eine Projektmappe oder ein Projekt unter quellcodeverwaltung geöffnet wird, wird die IDE das Quellcodeverwaltungs-VSPackage, das für die betreffende Projektmappe geladen werden festgelegt wurde.  
  
- Die Befehle im Menü des Datenquellen-Steuerelements VSPackage ausgeführt werden.  
  
  Ein VSPackage zu laden aller Komponenten sollten nur dann, wenn sie also sind werden benötigten Datenquellen-Steuerelement verwendet (andernfalls wird als verzögerte Laden).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Automatische Lösung-basierte VSPackages, austauschen  
 Sie können manuell austauschen, Datenquellen-Steuerelement VSPackages über die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Optionen** im Dialogfeld unter die **Quellcodeverwaltung** Kategorie. Automatische informationsreiche lösungsbasierte Paket austauschen bedeutet, dass ein Quellcodeverwaltungspaket, die für eine bestimmte Lösung festgelegt wurde automatisch auf aktiv festgelegt ist, wenn diese Projektmappe geöffnet wird. Jeder Quellcode-Verwaltungspaket sollte implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] der Wechsel zwischen den beiden behandelt source Control-Plug-ins (Implementieren der Source-Plug-in-API) und Datenquellen-Steuerelement VSPackages.  
  
 Das Quellcodeverwaltungspaket-Adapter wird verwendet, um alle Source Control-Plug-in-API-basierte wechseln-Plug-in. Der Prozess der Wechsel zu der intermediate Quellcodeverwaltungspaket Adapter und die Datenquellen-Steuerelement-Plug-in muss festgelegt werden, um, dass aktiv oder inaktiv für den Benutzer transparent ist. Das Paket Adapter ist immer aktiv, wenn Datenquellen-Steuerelement-Plug-in aktiv ist. Wechseln zwischen zwei Datenquellen-Steuerelement-Plug-ins Mengen, einfach zu laden und Entladen der DLL-Plug-in. Wechseln zu der ein Quellcodeverwaltungs-VSPackage, umfasst jedoch Interaktion mit der IDE auf die entsprechenden VSPackage zu laden.  
  
 Ein Datenquellen-Steuerelement wird VSPackage aufgerufen, wenn Projektmappe geöffnet ist und der Schlüssel für das VSPackage in der Projektmappendatei wird. Wenn die Projektmappe geöffnet wird, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sucht nach Wert des Registrierungsschlüssels und das entsprechende Quellcodeverwaltungs-VSPackage geladen. Alle Datenquellen-Steuerelement VSPackages müssen die oben beschriebenen Registrierungseinträge. Eine Lösung, die unter quellcodeverwaltung befindet, ist als eines bestimmten Quellcodeverwaltungs-VSPackage zugeordnet markiert. Datenquellen-Steuerelement, die VSPackages implementieren, muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> So aktivieren Sie die automatische Lösung-basierte VSPackage austauschen.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio-Benutzeroberfläche für die Paketauswahl "und" wechseln  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet eine Benutzeroberfläche für VSPackage-quellcodeverwaltung und Plug-in-Auswahl in der **Optionen** im Dialogfeld unter die **Quellcodeverwaltung** Kategorie. Es ermöglicht dem Benutzer die Auswahl für das aktive Quellcodeverwaltungs-Plug-in oder das VSPackage. Eine Dropdown-Liste enthält:  
  
- Alle installierten Quellcodeverwaltungspakete  
  
- Alle installierten Quellcodeverwaltungs-Plug-ins  
  
- Eine option "Keine", wodurch die quellcodeverwaltung deaktiviert  
  
  Nur die Benutzeroberfläche für die Auswahl des Steuerelements aktive Quelle wird angezeigt. Die VSPackage-Auswahl Blendet die Benutzeroberfläche für das vorherige VSPackage und zeigt die Benutzeroberfläche für die neue Ressourcengruppe ein. Das VSPackage aktive wird auf pro-Benutzer ausgewählt. Wenn ein Benutzer mehrere Kopien von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gleichzeitig öffnen, die jeweils können möglicherweise eine andere aktive VSPackage. Wenn auf demselben Computer mehrere Benutzer angemeldet sind, kann jeder Benutzer separate Instanzen des verfügen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] öffnen, jeweils mit einem anderen aktiven VSPackage. Wenn mehrere Instanzen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geschlossen werden, von einem Benutzer, die das Quellcodeverwaltungs-VSPackage, das für die zuletzt geöffnete Projektmappe das Standard-Datenquellen-Steuerelement VSPackage aktiv auf Neustart festgelegt werden wird, aktiv war.  
  
  Im Gegensatz zu früheren Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ein Neustart der IDE ist nicht mehr die einzige Möglichkeit, Datenquellen-Steuerelement VSPackages zu wechseln. VSPackage-Auswahl erfolgt automatisch. Wechseln Pakete erfordert Berechtigungen für Windows-Benutzers (nicht "Administrator" oder "Poweruser").  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funktionen](../../extensibility/internals/source-control-vspackage-features.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)

