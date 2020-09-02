---
title: Ressourcen in VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696092"
---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können lokalisierte Ressourcen in Native Satelliten-UI-DLLs, verwaltete Satelliten-DLLs oder in ein verwaltetes VSPackage einbinden.  
  
 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:  
  
- Zeichenfolgen  
  
- Paket Lade Schlüssel (auch Zeichen folgen)  
  
- Tool Fenster Symbole  
  
- Dateien für die kompilierte Befehls Tabellenausgabe (CTO)  
  
- CTO-Bitmaps  
  
- Befehlszeilen Hilfe  
  
- Informationen zu Dialogfeld Daten  
  
  Ressourcen in einem verwalteten Paket werden anhand der Ressourcen-ID ausgewählt. Eine Ausnahme ist die CTO-Datei, die mit dem Namen "ctmenu" benannt werden muss. Die CTO-Datei muss in der Ressourcen Tabelle als angezeigt werden `byte[]` . Alle anderen Ressourcen Elemente werden nach Typ identifiziert.  
  
  Sie können das- <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Attribut verwenden, um anzugeben, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dass verwaltete Ressourcen verfügbar sind.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Diese Einstellung gibt an, dass bei der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Suche nach Ressourcen von nicht verwaltete Satelliten-DLLs ignoriert werden soll, z. b. mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zwei oder mehr Ressourcen ermittelt, die dieselbe Ressourcen-ID aufweisen, wird die erste gefundene Ressource verwendet.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel ist eine verwaltete Darstellung eines Tool Fenster Symbols.  
  
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
  
 Im folgenden Beispiel wird veranschaulicht, wie das CTO-Bytearray einbettet wird, das als ctmenu benannt werden muss.  
  
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
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verzögert das Laden von VSPackages, wann immer dies möglich ist. Eine Folge der Einbettung einer CTO-Datei in ein VSPackage ist, dass [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alle VSPackages während des Setups in den Arbeitsspeicher laden müssen. Dies ist der Zeitpunkt, an dem eine zusammengeführte Befehls Tabelle erstellt wird. Ressourcen können aus einem VSPackage extrahiert werden, indem die Metadaten untersucht werden, ohne dass Code im VSPackage ausgeführt wird. Das VSPackage ist zu diesem Zeitpunkt nicht initialisiert, sodass der Leistungsverlust minimal ist.  
  
 Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nach der Installation eine Ressource von einem VSPackage anfordert, wird dieses Paket wahrscheinlich bereits geladen und initialisiert, sodass der Leistungsverlust minimal ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)
