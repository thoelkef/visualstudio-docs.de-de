---
title: Registrieren von Interop-Assembly-Befehls Handlern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724690"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrieren der Befehlshandler von Interop-Assemblys
Ein VSPackage muss bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registriert werden, damit die integrierte Entwicklungsumgebung (IDE) seine Befehle ordnungsgemäß weiterleitet.

 Die Registrierung kann entweder per manueller Bearbeitung oder mithilfe einer Registrierungsstelle (RGS-Datei) aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Das Managed Package Framework (MPF) stellt diese Funktionalität durch die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>-Klasse bereit.

- [Referenz Ressourcen des Befehls Tabellen Formats](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) befinden sich in nicht verwalteten Satelliten-UI-DLLs.

## <a name="command-handler-registration-of-a-vspackage"></a>Befehls Handler-Registrierung eines VSPackages
 Ein VSPackage, das als Handler für Benutzeroberflächen basierte Befehle fungiert, erfordert einen Registrierungs Eintrag namens nach dem VSPackage-`GUID`. Dieser Registrierungs Eintrag gibt den Speicherort der UI-Ressourcen Datei des VSPackages und die Menü Ressource in dieser Datei an. Der Registrierungs Eintrag selbst befindet sich unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \menüs, wobei *\<Version >* die Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist, z. b. 9,0.

> [!NOTE]
> Der Stammpfad von HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* kann mit einem alternativen Stamm überschrieben werden, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell initialisiert wird. Weitere Informationen zum Stammpfad finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Der ctmenu-Ressourcen Registrierungs Eintrag
 Die Struktur des Registrierungs Eintrags lautet:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> ist die `GUID` des VSPackage in der Form {xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx}.

 *\<Resource Informationen >* bestehen aus drei durch Kommas getrennten Elementen. Diese Elemente sind in der angegebenen Reihenfolge:

 \<*Pfad zur Ressourcen-DLL*->, \<*Menü Ressourcen-ID*>, \<*Menü Version* >

 In der folgenden Tabelle werden die Felder \<*Ressourcen Informationen*> beschrieben.

| Element | Beschreibung |
|---------------------------| - |
| \<*Pfad zur Ressourcen-DLL* > | Dies ist der vollständige Pfad zur Ressourcen-DLL, die die Menü Ressource enthält, oder diese ist leer. Dies gibt an, dass die Ressourcen-DLL des VSPackages verwendet werden soll (wie im Paket Unterschlüssel angegeben, in dem das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, dieses Feld leer zu lassen. |
| \<*Menü Ressourcen-ID* > | Dies ist die Ressourcen-ID der `CTMENU` Ressource, die alle Benutzeroberflächen Elemente für das VSPackage enthält, wie aus einer [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) -Datei kompiliert. |
| \<*Menü Version* > | Dies ist eine Zahl, die als Version für die `CTMENU` Ressource verwendet wird. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet diesen Wert, um zu bestimmen, ob der Inhalt der `CTMENU` Ressource mit dem Cache aller `CTMENU` Ressourcen neu zusammengeführt werden muss. Eine erneute Zusammenführung wird durch Ausführen des Befehls "Debug-Setup" ausgelöst.<br /><br /> Dieser Wert sollte zunächst auf 1 festgelegt und nach jeder Änderung in der `CTMENU` Ressource und vor dem erneuten zusammenführen erhöht werden. |

### <a name="example"></a>Beispiel
 Im folgenden finden Sie ein Beispiel für eine Reihe von Ressourcen Einträgen:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Siehe auch
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)