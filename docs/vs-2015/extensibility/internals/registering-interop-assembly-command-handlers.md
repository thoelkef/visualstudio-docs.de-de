---
title: Registrieren der Befehlshandler von Interop-Assembly | Microsoft-Dokumentation
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
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a087b5952b930145cd9f620a0eebeeee5d947149
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778591"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrieren der Befehlshandler von Interop-Assemblys
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine VSPackage muss zaregistrovat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , damit die integrierte Entwicklungsumgebung (IDE) seine Befehle ordnungsgemäß weiterleitet.  
  
 Die Registrierung kann entweder durch die manuelle Bearbeitung oder über eine Registrierungsstelle (.rgs)-Datei aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Das Managed Package Framework (MPF) stellt diese Funktionalität über die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Klasse.  
  
 [Tabelle Formatreferenz für Blobüberwachungsprotokolle Befehl](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) Ressourcen befinden sich im nicht verwalteten Satelliten-UI-Dlls.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Befehl Registrierung von VSPackages  
 Ein VSPackage als einen Handler für die Benutzeroberfläche (UI)-Basis Befehle erfordert einen Registrierungseintrag Namens nach dem VSPackage `GUID`. Dieser Registrierungseintrag gibt den Speicherort der Ressourcendatei für die VSPackage Benutzeroberfläche und die Menüressource innerhalb dieser Datei an. Der Registrierungseintrag selbst befindet sich unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version >* \Menus, wobei  *\<Version >* ist die Version des [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], z. B. 9.0.  
  
> [!NOTE]
>  Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann überschrieben werden, mit einer alternativen Stamm, wenn die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Shell initialisiert wird. Weitere Informationen zu den Stammpfad, finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Der Registrierungseintrag für CTMENU-Ressource  
 Die Struktur des Registrierungseintrags lautet:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> ist der `GUID` des VSPackage in der Form {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informationen zur Ressource >* besteht aus drei Elementen, die durch Kommas getrennt. Diese Elemente sind in der Reihenfolge auf:  
  
 \<*Pfad zur Ressourcen-DLL*>, \< *Menü-Ressourcen-ID*>, \< *Menü-Version*>  
  
 Die folgende Tabelle beschreibt die Felder der \< *Ressourceninformationen*>.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|\<*Pfad zur Ressourcen-DLL*>|Dies ist der vollständige Pfad zu den Ressourcen-DLL, die die Menüressource enthält oder diese leer gelassen, gibt an, dass die VSPackage Ressource DLL ist, verwendet werden (gemäß des Unterschlüssels "Pakete", in das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, die dieses Feld leer lassen.|  
|\<*Menü-Ressourcen-ID*>|Dies ist die Ressourcen-ID der `CTMENU` Ressource, die alle Elemente der Benutzeroberfläche für das VSPackage enthält, wie vom kompiliert einen [VSCT](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) Datei.|  
|\<*Menü-Version*>|Dies ist eine Zahl, die als einer Version für die `CTMENU` Ressource. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwendet diesen Wert um zu bestimmen, ob er den Inhalt der erneutes zusammenführen muss die `CTMENU` Ressource mit dem Cache aller `CTMENU` Ressourcen. Ein erneutes Zusammenführen wird ausgelöst, durch den Devenv-Setup-Befehl ausführen.<br /><br /> Dieser Wert sollte zunächst auf 1 festgelegt und nach jeder Änderung erhöht die `CTMENU` Ressource und vor der erneutes zusammenführen.|  
  
### <a name="example"></a>Beispiel  
 Hier ist ein Beispiel für eine Reihe von Ressourceneinträgen:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

