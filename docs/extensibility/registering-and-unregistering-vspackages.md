---
title: Registrieren und Aufheben der Registrierung von VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301584"
---
# <a name="register-and-unregister-vspackages"></a>VSPackages registrieren und abmelden
Sie verwenden Attribute, um ein VSPackage zu registrieren,

## <a name="register-a-vspackage"></a>Registrieren eines VSPackage
 Sie können Attribute verwenden, um die Registrierung von verwalteten VSPackages zu steuern. Alle Registrierungsinformationen sind in einer *.pkgdef-Datei* enthalten. Weitere Informationen zur dateibasierten Registrierung finden Sie unter [CreatePkgDef-Dienstprogramm](../extensibility/internals/createpkgdef-utility.md).

 Der folgende Code zeigt, wie Sie die Standardregistrierungsattribute verwenden, um Ihr VSPackage zu registrieren.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Aufheben der Registrierung einer Erweiterung
 Wenn Sie mit vielen verschiedenen VSPackages experimentiert haben und diese aus der experimentellen Instanz entfernen möchten, können Sie einfach den Befehl **Zurücksetzen** ausführen. Suchen Sie auf der Startseite Ihres Computers nach **Visual Studio Experimental Instance zurücksetzen,** oder führen Sie diesen Befehl über die Befehlszeile aus:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Wenn Sie eine Erweiterung deinstallieren möchten, die Sie auf Ihrer Entwicklungsinstanz von Visual Studio installiert haben, wechseln Sie zu > **Tools-Erweiterungen und Updates**, suchen Sie die Erweiterung, und klicken Sie auf **Deinstallieren**. **Tools**

 Wenn aus irgendeinem Grund keine dieser Methoden erfolgreich die Deinstallation der Erweiterung ermöglicht, können Sie die Registrierung der VSPackage-Assembly wie folgt von der Befehlszeile abheben:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung

In bestimmten Fällen müssen Sie möglicherweise ein neues Registrierungsattribut für Ihre Erweiterung erstellen. Sie können Registrierungsattribute verwenden, um neue Registrierungsschlüssel hinzuzufügen oder um vorhandenen Schlüsseln neue Werte hinzuzufügen. Das neue Attribut muss <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>von ableiten und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> die und-Methoden überschreiben.

### <a name="create-a-custom-attribute"></a>Erstellen eines benutzerdefinierten Attributs

Der folgende Code zeigt, wie Sie ein neues Registrierungsattribut erstellen.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Der <xref:System.AttributeUsageAttribute> wird für Attributklassen verwendet, um das Programmelement (Klasse, Methode usw.) anzugeben, zu dem sich das Attribut bezieht, ob es mehr als einmal verwendet werden kann und ob es vererbt werden kann.

### <a name="create-a-registry-key"></a>Erstellen eines Registrierungsschlüssels

Im folgenden Code erstellt das benutzerdefinierte Attribut einen **benutzerdefinierten** Unterschlüssel unter dem Schlüssel für das VSPackage, das registriert wird.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Erstellen eines neuen Werts unter einem vorhandenen Registrierungsschlüssel

Sie können einem vorhandenen Schlüssel benutzerdefinierte Werte hinzufügen. Der folgende Code zeigt, wie einem VSPackage-Registrierungsschlüssel ein neuer Wert hinzugefügt wird.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
