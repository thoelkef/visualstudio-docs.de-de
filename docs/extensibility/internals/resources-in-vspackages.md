---
title: Ressourcen in VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705605"
---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
Sie können lokalisierte Ressourcen in systemeigene Satelliten-UI-DLLs, verwaltete Satelliten-DLLs oder in ein verwaltetes VSPackage selbst einbetten.

 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:

- Zeichenfolgen

- Paketladeschlüssel (die auch Zeichenfolgen sind)

- Toolfenstersymbole

- Kompilierte Befehlstabellenausgabedateien (CTO)

- CTO-Bitmaps

- Befehlszeilenhilfe

- Informationen zu Dialogfelddaten

  Ressourcen in einem verwalteten Paket werden nach Ressourcen-ID ausgewählt. Eine Ausnahme ist die CTO-Datei, die den Namen CTMENU haben muss. Die CTO-Datei muss in der `byte[]`Ressourcentabelle als angezeigt werden. Alle anderen Ressourcenelemente werden nach Typ identifiziert.

  Sie können <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> das Attribut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden, um anzugeben, dass verwaltete Ressourcen verfügbar sind.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Die <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Einstellung auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diese Weise gibt an, dass nicht verwaltete Satelliten-DLLs ignoriert werden sollten, wenn nach Ressourcen gesucht wird, z. B. mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>von . Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwei oder mehr Ressourcen mit derselben Ressourcen-ID gefunden werden, wird die erste gefundene Ressource verwendet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel ist eine verwaltete Darstellung eines Symbols im Werkzeugfenster.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 Im folgenden Beispiel wird veranschaulicht, wie das CTO-Byte-Array einbettet wird, das den Namen CTMENU haben muss.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verzögert das Laden von VSPackages, wann immer möglich. Eine Folge des Einbettens einer CTO-Datei in ein VSPackage ist, dass [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alle diese VSPackages während des Setups in den Arbeitsspeicher geladen werden müssen, d. h., wenn eine zusammengeführte Befehlstabelle erstellt wird. Ressourcen können aus einem VSPackage extrahiert werden, indem die Metadaten untersucht werden, ohne Code im VSPackage auszuführen. Das VSPackage wird zu diesem Zeitpunkt nicht initialisiert, sodass der Leistungsverlust minimal ist.

 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine Ressource nach Setup von einem VSPackage anfordert, wird dieses Paket wahrscheinlich bereits geladen und initialisiert, sodass der Leistungsverlust minimal ist.

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
- [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
