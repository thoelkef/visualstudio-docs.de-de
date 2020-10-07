---
title: .NET Core-Unterstützung
description: Dieses Dokument behandelt die Unterstützung der .NET Core-Versionen in Visual Studio für Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 4009e6c139ef33bcd4caa01a9313695628757884
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583930"
---
# <a name="net-core-support"></a>.NET Core-Unterstützung

Die folgende Tabelle beschreibt die Versionen von .NET Core, die von den Stabil- und Preview-Versionen von Visual Studio für Mac unterstützt werden:

| .NET Core SDK-Version |Visual Studio für Mac 8.1 | Visual Studio für Mac 8.2 | Visual Studio für Mac 8.3 | Visual Studio für Mac 8.4 | Visual Studio für Mac 8.5 | Visual Studio für Mac 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 – v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 – v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v5.0 (Vorschau) | | | | | |✔︎|

> [!IMPORTANT]
> Vorschauversionen der .NET Core SDK werden nicht unterstützt. Führen Sie ein Update auf die veröffentlichte Version durch. Bei der Installation von Visual Studio für Mac 8.4 wird die freigegebene Version von .NET Core v3.1 installiert.

> [!IMPORTANT]
> Wenn Sie zuvor .NET Core v2.2.1xx mit Visual Studio für Mac 8.0 verwendet haben, müssen Sie ein manuelles Update auf die unterstützte .NET Core-Version durchführen (siehe die obige Tabelle). Es wird entweder [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) oder [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2) empfohlen.

* .NET Core v3.1 wird standardmäßig für die Versionen 8.4, 8.5 und 8.6 installiert.
* .NET Core v3.0 wird standardmäßig für 8.3 installiert.
* .NET Core Version 2.1.701 (Version 2.1.700 für 8.1) wird standardmäßig mit dem Installer installiert.
* Um eine andere Version von .NET Core herunterzuladen, besuchen Sie die [dotnet-Seite](https://dotnet.microsoft.com/download/dotnet-core).
* Bei Verwendung von .NET Core 3.0 wird standardmäßig C# Version 8 verwendet. C# 7.3 ist Standard bei der Verwendung von .NET Core 2.x. Weitere Informationen finden Sie unter [Verwaltung der C#-Sprachversion](/dotnet/csharp/language-reference/configure-language-version).
* Informationen zum Installieren einer Vorschauversion von Visual Studio für Mac finden Sie im Handbuch [Installieren einer Vorschauversion](./install-preview.md).