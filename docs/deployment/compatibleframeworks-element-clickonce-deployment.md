---
title: '&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06b96327205369d0280a865b632801edbf199745
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407863"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;CompatibleFrameworks&gt; -Element (ClickOnce-Bereitstellung)
Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.

> [!NOTE]
> [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) unterstützt nicht die `compatibleFrameworks` -Element, wenn ein Anwendungsmanifest, das Speichern von wurde bereits mit einem Zertifikat signiert [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Stattdessen müssen Sie [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) verwenden.

## <a name="syntax"></a>Syntax

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Die `compatibleFrameworks` Element ist erforderlich, für die Bereitstellungsmanifeste der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime gebotenen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höher. Die `compatibleFrameworks` Element enthält ein oder mehrere `framework` Elemente, die .NET Framework-Versionen angeben, auf denen diese Anwendung ausgeführt werden kann. Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime wird die Anwendung ausgeführt, auf dem ersten verfügbaren `framework` in dieser Liste.

 In der folgende Tabelle werden die Attribute aufgeführt, die die `compatibleFrameworks` Element unterstützt.

|Attribut|Beschreibung|
|---------------|-----------------|
|`S` `upportUrl`|Dies ist optional. Gibt eine URL, in denen die bevorzugte kompatible .NET Framework-Version heruntergeladen werden kann.|

## <a name="framework"></a>Framework
 Erforderlich. Die folgende Tabelle enthält die Attribute, die die `framework` Element unterstützt.

|Attribut|Beschreibung|
|---------------|-----------------|
|`targetVersion`|Erforderlich. Gibt die Versionsnummer des .NET Framework-Ziel an.|
|`profile`|Erforderlich. Gibt das Profil von .NET Framework-Ziel.|
|`supportedRuntime`|Erforderlich. Gibt die Versionsnummer der Laufzeit mit dem Ziel .NET Framework verknüpft ist.|

## <a name="remarks"></a>Hinweise

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel zeigt eine `compatibleFrameworks` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Diese Bereitstellung ausgeführt werden kann, auf die [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Es kann auch ausgeführt, auf die [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , da es sich um eine Obermenge ist die [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)