---
title: Registrierung und Auswahl (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705719"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrierung und Auswahl (Quellcodeverwaltungs-VSPackage)
Ein Quellcodeverwaltungs-VSPackage muss registriert sein, um es für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügbar zu machen. Wenn mehr als ein Quellcodeverwaltungs-VSPackage registriert ist, kann der Benutzer auswählen, welches VSPackage zu den entsprechenden Zeiten geladen werden soll. Weitere Informationen zu VSPackages und deren Registrierung finden Sie unter [VSPackages.](../../extensibility/internals/vspackages.md)

## <a name="registering-a-source-control-package"></a>Registrieren eines Quellcodeverwaltungspakets
 Das Quellcodeverwaltungspaket ist registriert, damit die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung es finden und nach den unterstützten Features abfragen kann. Dies entspricht einem Verzögerungsladeschema, in dem eine Instanz eines Pakets nur erstellt wird, wenn seine Features oder Befehle erforderlich sind oder explizit angefordert werden.

 VSPackages platzieren Informationen in einem versionsspezifischen Registrierungsschlüssel,\\HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio*X.Y*, wobei *X* die Hauptversionsnummer und *Y* die Nebenversionsnummer ist. Diese Vorgehensweise bietet die Möglichkeit, die nebeneinander gehende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Installation mehrerer Versionen von zu unterstützen.

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche (UI) unterstützt die Auswahl aus mehreren installierten Quellcodeverwaltungs-Plug-Ins (über das Quellcodeverwaltungsadapterpaket) sowie Quellcodeverwaltung VSPackages. Es kann jeweils nur ein aktives Quellcodeverwaltungs-Plug-In oder VSPackage vorhanden sein. Wie unten beschrieben, ermöglicht die IDE jedoch das Wechseln zwischen Quellcodeverwaltungs-Plug-Ins und VSPackages über einen automatischen lösungsbasierten Paket-Swap-Mechanismus. Es gibt einige Anforderungen seitens des Quellcodeverwaltungs-VSPackage, um diesen Auswahlmechanismus zu aktivieren.

### <a name="registry-entries"></a>Registrierungseinträge
 Ein Quellcodeverwaltungspaket benötigt drei private GUIDs:

- Paket-GUID: Dies ist die Haupt-GUID für das Paket, das die Quellcodeverwaltungsimplementierung enthält (in diesem Abschnitt ID_Package genannt).

- Quellcodeverwaltungs-GUID: Dies ist eine GUID für die Quellcodeverwaltung VSPackage, die zum Registrieren im Visual Studio Source Control Stub verwendet wird, und wird auch als Befehls-UI-Kontext-GUID verwendet. Die Quellcodeverwaltungsdienst-GUID wird unter der Quellcodeverwaltungs-GUID registriert. Im Beispiel wird die Quellcodeverwaltungs-GUID ID_SccProvider aufgerufen.

- Quellcodeverwaltungsdienst-GUID: Dies ist die private Dienst-GUID, die von Visual Studio verwendet wird (in diesem Abschnitt SID_SccPkgService genannt). Darüber hinaus muss das Quellcodeverwaltungspaket weitere GUIDs für VSPackages, Toolfenster usw. definieren.

  Die folgenden Registrierungseinträge müssen von einem Quellcodeverwaltungs-VSPackage vorgenommen werden:

| Schlüsselname | Einträge |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (Standard) = rg_sz ID_SccProvider: |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (Standard) =\<rg_sz: Freundlicher Name von Package><br /><br /> Dienst = rg_sz SID_SccPkgService: |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (Standard) = rg_sz:-\<Ressourcen-ID für lokalisierte><br /><br /> Paket = rg_sz ID_Package: |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Beachten Sie, `SourceCodeControl`dass der Schlüsselname [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , bereits von verwendet \<wird und nicht als Auswahl für PackageName> verfügbar ist.) | (Standard) = rg_sz ID_Package: |

## <a name="selecting-a-source-control-package"></a>Auswählen eines Quellcodeverwaltungspakets
 Mehrere Quellcodeverwaltungs-Plug-In-API-basierte Plug-Ins und Quellcodeverwaltungs-VSPackages können gleichzeitig registriert werden. Bei der Auswahl eines Quellcodeverwaltungs-Plug-Ins [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oder VSPackage muss sichergestellt werden, dass das Plug-In oder VSPackage zum richtigen Zeitpunkt geladen wird, und das Laden unnötiger Komponenten aufschieben kann, bis sie erforderlich sind. Darüber [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hinaus müssen alle Benutzeroberflächen aus anderen inaktiven VSPackages, einschließlich Menüelementen, Dialogfeldern und Symbolleisten, entfernt und die Benutzeroberfläche für das aktive VSPackage angezeigt werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lädt ein Quellcodeverwaltungs-VSPackage, wenn einer der folgenden Vorgänge ausgeführt wird:

- Die Lösung wird geöffnet (wenn die Lösung unter Quellcodeverwaltung steht).

   Wenn eine Projektmappe oder ein Projekt unter Quellcodeverwaltung geöffnet wird, bewirkt die IDE, dass das für diese Projektmappe vorgesehene Quellcodeverwaltungs-VSPackage geladen wird.

- Alle Menübefehle der Quellcodeverwaltung VSPackage werden ausgeführt.

  Ein Quellcodeverwaltungs-VSPackage sollte alle Komponenten, die es benötigt, nur laden, wenn sie tatsächlich verwendet werden (auch als verzögertes Laden bezeichnet).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatisches lösungsbasiertes VSPackage Swapping
 Sie können die Quellcodeverwaltung VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manuell über das Dialogfeld **Optionen** unter der Kategorie **Quellcodeverwaltung** austauschen. Automatisches lösungsbasiertes Paketaustausch bedeutet, dass ein Quellcodeverwaltungspaket, das für eine bestimmte Lösung festgelegt wurde, automatisch auf aktiv gesetzt wird, wenn diese Lösung geöffnet wird. Jedes Quellcodeverwaltungspaket <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> sollte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>implementieren und . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]behandelt den Switch zwischen den beiden Quellcodeverwaltungs-Plug-Ins (Implementierung der Quellcodeverwaltungs-Plug-In-API) und der Quellcodeverwaltung VSPackages.

 Das Quellcodeverwaltungsadapterpaket wird verwendet, um zu jedem Quellsteuerungs-Plug-In-API-basierten Plug-In zu wechseln. Der Vorgang des Wechsels zum Zwischenpaket für die Quellcodeverwaltung und das Bestimmen, welches Quellcodeverwaltungs-Plug-In auf aktiv oder inaktiv eingestellt sein muss, ist für den Benutzer transparent. Das Adapterpaket ist immer aktiv, wenn ein Quellcodeverwaltungs-Plug-In aktiv ist. Das Umschalten zwischen zwei Quellcodeverwaltungs-Plug-Ins bedeutet, die Plug-In-DLL einfach zu laden und zu entladen. Das Umschalten zu einem Quellcodeverwaltungs-VSPackage erfordert jedoch die Interaktion mit der IDE, um das entsprechende VSPackage zu laden.

 Ein Quellcodeverwaltungs-VSPackage wird aufgerufen, wenn eine Lösung geöffnet wird und sich der Registrierungsschlüssel für das VSPackage in der Projektmappendatei befindet. Wenn die Lösung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet wird, sucht den Registrierungswert und lädt das entsprechende Quellcodeverwaltungs-VSPackage. Alle Quellcodeverwaltung VSPackages muss die oben beschriebenen Registrierungseinträge haben. Eine Lösung, die sich unter Quellcodeverwaltung befindet, wird als einem bestimmten Quellcodeverwaltungs-VSPackage zugeordnet markiert. Quellcodeverwaltung VSPackages muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> die implementieren, um den automatischen lösungsbasierten VSPackage-Austausch zu ermöglichen.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio-Benutzeroberfläche für Paketauswahl und -umschaltung
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet eine Benutzeroberfläche für die Quellcodeverwaltung VSPackage und die Plug-In-Auswahl im Dialogfeld **Optionen** unter der Kategorie **Quellcodeverwaltung.** Es ermöglicht dem Benutzer, das aktive Quellcodeverwaltungs-Plug-In oder VSPackage auszuwählen. Eine Dropdown-Liste enthält:

- Alle installierten Quellcodeverwaltungspakete

- Alle installierten Quellcodeverwaltungs-Plug-Ins

- Eine "Keine"-Option, die die Quellcodeverwaltung deaktiviert

  Nur die Benutzeroberfläche für die aktive Quellcodeverwaltungsauswahl ist sichtbar. Die VSPackage-Auswahl blendet die Benutzeroberfläche für das vorherige VSPackage aus und zeigt die Benutzeroberfläche für das neue an. Das aktive VSPackage wird benutzerspezifisch ausgewählt. Wenn ein Benutzer mehrere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kopien gleichzeitig geöffnet hat, kann jede eine andere aktive VSPackage verwenden. Wenn mehrere Benutzer am gleichen Computer angemeldet sind, kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jeder Benutzer separate Instanzen öffnen, die jeweils mit einem anderen aktiven VSPackage vorhanden sind. Wenn mehrere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Instanzen von einem Benutzer geschlossen werden, wird das Quellcodeverwaltungs-VSPackage, das für die letzte geöffnete Lösung aktiv war, zum Standardquellcodesteuerelement VSPackage, das beim Neustart aktiv eingestellt werden soll.

  Im Gegensatz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu früheren Versionen von ist ein IDE-Neustart nicht mehr die einzige Möglichkeit, die Quellcodeverwaltung VSPackages zu wechseln. Die VSPackage-Auswahl erfolgt automatisch. Das Umschalten von Paketen erfordert Windows-Benutzerrechte (nicht Administrator oder Hauptbenutzer).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Features](../../extensibility/internals/source-control-vspackage-features.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
