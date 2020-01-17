---
title: .NET Core-Unterstützung
description: Dieses Dokument behandelt die Unterstützung der .NET Core-Versionen in Visual Studio für Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 6a4bc5a68a17bf3562e0f82b1f2c521f9b3f3e72
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75735804"
---
# <a name="net-core-support"></a>.NET Core-Unterstützung

Die folgende Tabelle beschreibt die Versionen von .NET Core, die von den Stabil- und Preview-Versionen von Visual Studio für Mac unterstützt werden:

| .NET Core SDK-Version |Visual Studio für Mac 8.1 (Stabil) | Visual Studio für Mac 8.2 (Stabil) | Visual Studio für Mac 8.3 (Stabil) | Visual Studio für Mac 8.4 (Stabil)
|---------|---------|---------|---------|---------|
|v2.1.0 – v2.1.5xx | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|
|v2.2.1 – v2.2.1xx | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|
|v3.1 | | | |✔︎|

> [!IMPORTANT]
> Vorschauversionen der .NET Core SDK werden nicht unterstützt. Führen Sie ein Update auf die veröffentlichte Version durch. Bei der Installation von Visual Studio für Mac 8.4 wird die freigegebene Version von .NET Core v3.1 installiert.

> [!IMPORTANT]
> Wenn Sie zuvor .NET Core v2.2.1xx mit Visual Studio für Mac 8.0 verwendet haben, müssen Sie ein manuelles Update auf die unterstützte .NET Core-Version durchführen (siehe die obige Tabelle). Es wird entweder [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) oder [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2) empfohlen.

* .NET Core v3.1 wird standardmäßig für 8.4 installiert.
* .NET Core v3.0 wird standardmäßig für 8.3 installiert.
* .NET Core Version 2.1.701 (Version 2.1.700 für 8.1) wird standardmäßig mit dem Installer installiert.
* Um eine andere Version von .NET Core herunterzuladen, besuchen Sie die [dotnet-Seite](https://dotnet.microsoft.com/download/dotnet-core).
* Bei Verwendung von .NET Core 3.0 wird standardmäßig C# Version 8 verwendet. C# 7.3 ist Standard bei der Verwendung von .NET Core 2.x. Weitere Informationen finden Sie unter [Verwaltung der C#-Sprachversion](/dotnet/csharp/language-reference/configure-language-version).
* Informationen zum Installieren einer Vorschauversion von Visual Studio für Mac finden Sie im Handbuch [Installieren einer Vorschauversion](/visualstudio/mac/install-preview).
