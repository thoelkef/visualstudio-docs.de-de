---
title: Registrieren von Interop-Assembly Befehlshandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4b2c0d40029cbc84d64a4ffe5ee50c59c893b95
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrierung der Befehlshandler der Interop-Assembly
Eine VSPackage muss mit registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit der integrierten Entwicklungsumgebung (IDE) die zugehörigen Befehle ordnungsgemäß weiterleitet.  
  
 Die Registrierung kann entweder durch die manuelle Bearbeitung oder über eine Registrierungsstelle (.rgs)-Datei aktualisiert werden. Weitere Informationen finden Sie unter [Registrierungsskripte erstellen](/cpp/atl/creating-registrar-scripts).  
  
 Das Managed Package Framework (MPF) stellt diese Funktionalität über die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Klasse.  
  
 [Befehl Format Tabellenverweis](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) Ressourcen befinden sich in nicht verwalteten Satelliten-Dlls UI.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Befehl-Registrierung von VSPackages  
 Ein VSPackage als einen Handler für die Benutzeroberfläche (UI)-Basis Befehle ist erforderlich, einen Registrierungeintrag Namens nach dem VSPackage `GUID`. Dieser Registrierungseintrag gibt den Speicherort der Ressourcendatei für die VSPackage Benutzeroberfläche und die Menüressource innerhalb dieser Datei. Der Registrierungseintrag selbst befindet sich unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version >*\Menus, wobei  *\<Version >* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 9.0.  
  
> [!NOTE]
>  Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann überschrieben werden, mit einer alternativen root, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell initialisiert wird. Weitere Informationen zu den Stammpfad, finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Der Registrierungseintrag für CTMENU-Ressource  
 Die Struktur des Registrierungseintrags ist:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> ist der `GUID` des VSPackage im Format {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informationen zur Ressource >* besteht aus drei Elementen, die durch Kommas getrennt. Diese Elemente sind in der Reihenfolge auf:  
  
 \<*Pfad zur Ressourcen-DLL*>, \< *Menü-Ressourcen-ID*>, \< *Menü-Version*>  
  
 Die folgende Tabelle beschreibt die Felder der \< *Ressourceninformationen*>.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|\<*Pfad zur Ressourcen-DLL*>|Dies ist der vollständige Pfad zu den Ressourcen-DLL, die die Menüressource enthält, oder dies ist leer, gibt an, dass die VSPackage Ressource DLL ist, verwendet werden (gemäß im Unterschlüssel Pakete, in das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, um dieses Feld leer lassen.|  
|\<*Menü-Ressourcen-ID*>|Dies ist die Ressourcen-ID, der die `CTMENU` Ressource, die alle Elemente der Benutzeroberfläche für das VSPackage enthält, wie aus kompiliert eine [VSCT](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) Datei.|  
|\<*Menü-Version*>|Dies ist eine Zahl, die als einer Version für die `CTMENU` Ressource. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dieser Wert verwendet, um festzustellen, ob es muss sich um den Inhalt der erneutes Zusammenführen von der `CTMENU` Ressource mit dem Cache aller `CTMENU` Ressourcen. Ein erneutes Zusammenführen von wird durch Ausführen des Setup-Befehls Devenv ausgelöst.<br /><br /> Dieser Wert anfangs auf 1 festgelegt und nach jeder Änderung erhöht die `CTMENU` Ressource und bevor die erneutes Zusammenführen von auftritt.|  
  
### <a name="example"></a>Beispiel  
 Hier ist ein Beispiel für eine Reihe von Ressourceneinträge:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)