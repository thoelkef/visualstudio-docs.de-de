---
title: Registrieren von Interop Assembly Command Handlern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705863"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrieren der Befehlshandler von Interop-Assemblys
Ein VSPackage muss [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich registrieren, damit die integrierte Entwicklungsumgebung (IDE) ihre Befehle ordnungsgemäß weiterleitet.

 Die Registrierung kann entweder manuell bearbeitet oder mithilfe einer Registrardatei (.rgs) aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Das Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> stellt diese Funktionalität über die Klasse bereit.

- [Befehlstabellenformat Referenzressourcen](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) befinden sich in nicht verwalteten Satelliten-UI-Dlls.

## <a name="command-handler-registration-of-a-vspackage"></a>Befehlshandlerregistrierung eines VSPackage
 Ein VSPackage, das als Handler für Benutzeroberflächenbefehle fungiert, erfordert einen `GUID`Registrierungseintrag, der nach dem VSPackage benannt ist. Dieser Registrierungseintrag gibt den Speicherort der BENUTZERoberflächenressourcendatei des VSPackage und die Menüressource in dieser Datei an. Der Registrierungseintrag selbst befindet sich unter HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio-Version\\*\<>*,Menüs, wobei * \<Version>* die Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ist, z. B. 9.0.

> [!NOTE]
> Der Stammpfad der HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-Version\\*\<>* kann mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einem alternativen Stamm überschrieben werden, wenn die Shell initialisiert wird. Weitere Informationen zum Stammpfad finden Sie unter [Installieren von VSPackages with Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Der CTMENU-Ressourcenregistrierungseintrag
 Die Struktur des Registrierungseintrags ist:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` ist das VSPackage in der Form "XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX".

 Resource Information>besteht aus drei Elementen, die durch Kommas getrennt sind. * \<* Diese Elemente sind in der Reihenfolge:

 \<*Pfad zu Resource DLL*>, \< \< *Menüressourcen-ID*>, *Menüversion*>

 In der folgenden Tabelle \<werden die Felder von *Resource Information*> beschrieben.

| Element | BESCHREIBUNG |
|---------------------------| - |
| \<*Pfad zur Ressourcen-DLL*> | Dies ist der vollständige Pfad zur Ressourcen-DLL, die die Menüressource enthält, oder dies bleibt leer, was darauf hinweist, dass die Ressourcen-DLL des VSPackage verwendet werden soll (wie in der Unterschlüsselpaketen angegeben, in der das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, dieses Feld leer zu lassen. |
| \<*MenüRessourcen-ID*> | Dies ist die `CTMENU` Ressourcen-ID der Ressource, die alle UI-Elemente für das VSPackage enthält, wie sie aus einer [.vsct-Datei](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) kompiliert wurden. |
| \<*Menüversion*> | Dies ist eine Zahl, `CTMENU` die als Version für die Ressource verwendet wird. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet diesen Wert, um zu bestimmen, ob `CTMENU` der Inhalt der `CTMENU` Ressource mit dem Cache aller Ressourcen wieder aufgewirkt werden muss. Ein Remerge wird ausgelöst, indem der Befehl devenv setup ausgeführt wird.<br /><br /> Dieser Wert sollte zunächst auf 1 gesetzt und `CTMENU` nach jeder Änderung der Ressource und vor dem Remerge erhöht werden. |

### <a name="example"></a>Beispiel
 Hier ist ein Beispiel für ein paar Ressourceneinträge:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
