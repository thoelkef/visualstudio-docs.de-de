---
title: "Registrierung der Befehlshandler Interop-Assembly | Microsoft Docs"
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
  - "Interop-Assemblys, Befehlshandler"
  - "Befehlsbehandlung mit Interop-Assemblys, registrieren"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrierung der Befehlshandler Interop-Assembly
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage mit registrieren muss [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] damit die integrierte Entwicklungsumgebung \(IDE\) seine Befehle ordnungsgemäß weiterleitet.  
  
 Die Registrierung kann entweder durch die manuelle Bearbeitung oder mithilfe einer Registrierungsstelle \(.rgs\)\-Datei aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
 Managed Package Framework \(MPF\) bietet diese Funktionen durch die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Klasse.  
  
 [Command Table Format Reference](http://msdn.microsoft.com/de-de/09e9c6ef-9863-48de-9483-d45b7b7c798f) Ressourcen befinden sich in nicht verwalteten Satelliten\-Dlls Benutzeroberfläche.  
  
## Befehl Handler Registrierung von einem VSPackage  
 Ein VSPackage agiert als Handler für die Benutzeroberfläche \(UI\)\-basierenden Befehle erfordert einen Registrierungseintrag mit dem Namen des VSPackages `GUID`. Dieser Registrierungseintrag gibt den Speicherort des VSPackage\-UI\-Ressourcendatei und die Ressource in der Datei. Der Registrierungseintrag selbst befindet sich unter HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\Menus, wobei *\< Version \>* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 9.0.  
  
> [!NOTE]
>  Der Stammpfad der HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< Version \>* kann überschrieben werden, durch eine alternative root, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell wird initialisiert. Weitere Informationen zu den Stammpfad, finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### Der Registrierungseintrag für CTMENU\-Ressource  
 Die Struktur des Registrierungseintrags ist:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> ist der `GUID` des VSPackage im Format {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}.  
  
 *\< Ressourceninformationen \>* besteht aus drei Elementen, die durch Kommas getrennt. Diese Elemente sind in der Reihenfolge auf:  
  
 \<*Pfad zur Ressourcen\-DLL*\>, \<*Menü\-Ressourcen\-ID*\>, \<*Menü Version*\>  
  
 Die folgende Tabelle beschreibt die Felder der \<*Ressourceninformationen*\>.  
  
|Element|Beschreibung|  
|-------------|------------------|  
|\<*Pfad zur Ressourcen\-DLL*\>|Dies ist der vollständige Pfad zu der Ressourcen\-DLL, die die Ressource enthält, oder dies ist leer, gibt an, dass das VSPackage\-Ressource DLL ist, verwendet werden \(wie in den Paketen Unterschlüssel dem VSPackage selbst registriert angegeben\).<br /><br /> Es ist üblich, dieses Feld leer lassen.|  
|\<*Menü\-Ressourcen\-ID*\>|Dies ist die Ressourcen\-ID der `CTMENU` Ressource, die alle Elemente der Benutzeroberfläche für VSPackage enthält, wie anhand einer [VSCT](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) Datei.|  
|\<*Menü Version*\>|Dies ist eine Zahl, die als einer Version für die `CTMENU` Ressource.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet diesen Wert, um festzustellen, ob sie den Inhalt der erneutes Zusammenführen von muss die `CTMENU` Ressource mit dem Cache aller `CTMENU` Ressourcen. Ein erneutes Zusammenführen von wird durch Ausführen des Setup\-Befehls Devenv ausgelöst.<br /><br /> Dieser Wert anfangs auf 1 festgelegt und nach jeder Änderung erhöht die `CTMENU` Ressource und bevor die erneutes Zusammenführen von auftritt.|  
  
### Beispiel  
 Hier ist ein Beispiel für eine Reihe von Ressourceneinträgen:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle und Menüs, die mithilfe von Interop\-Assemblys](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)