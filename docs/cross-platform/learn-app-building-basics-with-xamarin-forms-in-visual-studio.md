---
title: Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 6cc569c2e58ef29f9e9372acad30c0c2df96466c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495959"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio

Nachdem Sie die Schritte in [Setup und Installation](../cross-platform/setup-and-install.md) und [Überprüfen Ihrer Xamarin-Umgebung](../cross-platform/verify-your-xamarin-environment.md) ausgeführt haben, veranschaulicht diese exemplarische Vorgehensweise das Erstellen einer einfachen App mit Xamarin.Forms. Mit Xamarin.Forms wird Ihr gesamter Benutzeroberflächencode einmal in eine .NET Standard-Klassenbibliothek geschrieben. Xamarin rendert dann automatisch die nativen UI-Steuerelemente für die iOS-, Android- und universelle Windows-Plattform.

Normalerweise ist es besser, eine .NET Standard-Bibliothek als ein Shared-Projekt für diesen gemeinsamen Code zu verwenden. Die .NET Standard-Bibliothek enthält die .NET-APIs, die auf allen Zielplattformen laufen können.

Hier ist die Anwendung, die Sie erstellen werden. Sie läuft (von links nach rechts) auf iOS- und Android-Smartphones sowie auf der Universellen Windows-Plattform (UWP) von Windows 10:

[![Beispiel für eine Wetter-App unter iOS, Android und Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Plattformübergreifender Leitfaden für Xamarin.Forms – 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Die Erstellung dieser Anwendung umfasst folgende Schritte:

-   [Einrichten der Projektmappe](#solution)

-   [Schreiben von freigegebenem Datendienstcode](#dataservice)

-   [Schreiben von freigegebenem Benutzeroberflächencode](#uicode)

-   [Testen der App mit dem Visual Studio-Emulator für Android](#test)

-   [Fertigstellen der Benutzeroberfläche mit einem homogenen Aussehen und Verhalten über Plattformen hinweg](#finish)

> [!TIP]
> Den vollständigen Quellcode dieses Projekts finden Sie im [Repository „xamarin-forms-samples“ auf GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

<a name="solution" />

## <a name="set-up-your-solution"></a>Einrichten der Projektmappe

Mit diesen Schritten erstellen Sie eine Xamarin.Forms-Projektmappe, die eine .NET Standard-Klassenbibliothek für freigegebenen Code und zwei zusätzliche NuGet-Pakete enthält.

1. Erstellen Sie in Visual Studio eine neue Projektmappe mit der Vorlage **Plattformübergreifende App (Xamarin.Forms)**, und nennen Sie diese **WeatherApp**. Suchen Sie dazu die Vorlage, indem Sie in der Liste auf der linken Seite **Visual C#** und **Plattformübergreifend** auswählen.

    ![Erstellen eines neuen plattformübergreifenden Xamarin.Forms-App-Projekts](../cross-platform/media/crossplat-xamarin-formsguide-2.png "Plattformübergeifender Leitfaden für Xamarin.Forms – 2")

    Wenn Sie die Vorlage dort nicht finden, müssen Sie möglicherweise Xamarin installieren oder das Visual Studio 2017-Feature aktivieren. Siehe [Setup und Installation](../cross-platform/setup-and-install.md).

2.  Nachdem Sie auf **OK** geklickt haben, können Sie einige Optionen auswählen. Wählen Sie **Leere App** und **.NET Standard** aus:

    ![Erstellen eines neuen plattformübergreifenden App-Projekts](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")

3.  Nachdem Sie auf **OK** geklickt haben, um die Projektmappe zu erstellen, verfügen Sie über eine Projektmappe mit vier Projekten:

    -   **WeatherApp**: Die .NET Standard-Bibliothek, in die Sie mit Xamarin.Forms Code schreiben, der plattformübergreifend freigegeben wird, einschließlich allgemeiner Geschäftslogik und Benutzeroberflächencode

    -   **WeatherApp.Android**: Das Projekt, das den nativen Android-Code enthält

    -   **WeatherApp.iOS**: das Projekt, das den systemeigenen iOS-Code enthält.

    -   **WeatherApp.UWP**: das Projekt, das Windows 10 UWP-Code enthält.

    > [!NOTE]
    >  Natürlich können Sie die Projekte für Plattformen löschen, die Sie nicht als Zielplattform vorgesehen haben.

     Innerhalb eines nativen Projekts haben Sie Zugriff auf den nativen Designer für die entsprechende Plattform und können nach Bedarf plattformspezifische Anzeigen und Funktionen implementieren.

4.  Aktualisieren Sie das Xamarin.Forms-NuGet-Paket in der Projektmappe wie folgt auf die neueste stabile Version:

    -   Wählen Sie **Tools > NuGet-Paket-Manager > NuGet-Pakete für Projektmappe verwalten** aus.

    -   Aktivieren Sie auf der Registerkarte **Updates** das **Xamarin.Forms**-Paket für alle Projekte in der Projektmappe. (Wählen Sie keine Updates für die Xamarin Android-Unterstützungsbibliotheken aus.)

    -   Aktualisieren Sie das Feld **Version** auf die **neueste stabile** Version, die verfügbar ist.

    -   Klicken Sie auf **Installieren**.

         ![Aktualisieren des Xamarin.Forms NuGet-Pakets](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

    Sie sollten es sich zur Gewohnheit machen, die Xamarin.Forms-Version zu aktualisieren, wenn Sie eine neue Xamarin.Forms-Projektmappe erstellen. Aktualisieren Sie keine Android-Unterstützungsbibliotheken. Diese Bibliotheken werden bei Bedarf aktualisiert, wenn Sie die Xamarin.Forms-Version aktualisieren.

5.  Fügen Sie das NuGet-Paket **Newtonsoft.Json** zu dem Projekt **WeatherApp** hinzu. Diese Bibliothek wird zum Verarbeiten der Informationen von einem Wetterdatendienst verwendet:

    -   Wählen Sie im (aus Schritt 4 noch geöffneten) NuGet-Paket-Manager die Registerkarte **Durchsuchen** aus, und suchen Sie nach **Newtonsoft**.

    -   Wählen Sie **Newtonsoft.Json**aus.

    -   Aktivieren Sie das **WeatherApp**-Projekt, welches das einzige Projekt ist, in dem Sie das Paket installieren müssen.

    -   Stellen Sie sicher, dass das **Version** -Feld auf die **neueste stabile** Version festgelegt ist.

    -   Klicken Sie auf **Installieren**.

    ![Suchen und Installieren des Newtonsoft.Json NuGet-Pakets](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

6.  Wiederholen Sie Schritt 5, um das **Microsoft.CSharp**-Paket im .NET Standard-Projekt zu suchen und zu installieren. Diese Bibliothek wird benötigt, um den C#-`dynamic`-Datentyp in einer .NET Standard-Bibliothek zu verwenden.

7.  Erstellen Sie die Projektmappe, und vergewissern Sie sich, dass keine Buildfehler aufgetreten sind.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Schreiben von freigegebenem Datendienstcode

Im **WeatherApp**-Projekt mit der .NET Standard-Bibliothek schreiben Sie Code, der plattformübergreifend verwendet wird. Diese Bibliothek wird von iOS-, Android- und Windows-Projekten erstellten App-Paketen referenziert.

Registrieren Sie sich unter [http://openweathermap.org/appid](http://openweathermap.org/appid) für einen kostenlosen API-Schlüssel, um dieses Beispiel auszuführen.

Mit den folgenden Schritten fügen Sie nun Code zu der .NET Standard-Bibliothek hinzu, um auf Daten dieses Wetterdiensts zuzugreifen und diese zu speichern:

1.  Klicken Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt, und wählen Sie **Hinzufügen > Klasse…** aus. Geben Sie der Datei im Dialogfeld **Neues Element hinzufügen** den Namen **Weather.cs**. Sie nutzen diese Klasse später, um Daten aus dem Wetterdatendienst zu speichern.

2.  Ersetzen Sie den gesamten Inhalt von *Weather.cs* durch folgenden Code:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

3.  Fügen Sie eine weitere Klasse zum **WeatherApp**-Projekt mit dem Namen **DataService.cs** hinzu, die Sie zum Verarbeiten von JSON-Daten aus dem Wetterdatendienst verwenden.

4.  Ersetzen Sie den gesamten Inhalt von **DataService.cs** durch folgenden Code:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5.  Fügen Sie eine dritte Klasse zum **WeatherApp**-Projekt mit dem Namen **Core.cs** hinzu, in der Sie die freigegebene Geschäftslogik einfügen. Dieser Code erstellt unter Verwendung einer Postleitzahl eine Abfragezeichenfolge, die den Wetterdienst aufruft, und füllt eine Instanz der Klasse `Weather` auf.

6.  Ersetzen Sie den Inhalt von **Core.cs** durch folgenden Code:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. Ersetzen Sie *YOUR API KEY HERE* durch den API-Schlüssel, den Sie erhalten haben. Er muss noch in Anführungszeichen stehen.

8.  Erstellen Sie das Bibliotheksprojekt **WeatherApp**, um sicherzustellen, dass der Code korrekt ist.

 <a name="uicode" />

## <a name="begin-writing-shared-ui-code"></a>Schreiben von freigegebenem Benutzeroberflächencode

Mit Xamarin.Forms können Sie freigegebenen Benutzeroberflächencode in der .NET Standard-Bibliothek implementieren. In den folgenden Schritten fügen Sie zum Projekt eine Seite mit einer Schaltfläche hinzu. Diese Schaltfläche aktualisiert den Text auf der Seite mit den vom Wetterdienst zurückgegebenen Daten, die Sie im vorherigen Abschnitt gesehen haben:

1.  Fügen Sie eine **Inhaltsseite** mit dem Namen **WeatherPage** hinzu, indem Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt klicken und **Hinzufügen > Neues Element...** auswählen. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Inhaltsseite** aus. Wählen Sie keine **Inhaltsseite (C#)** oder **Inhaltsansicht** aus. Nennen Sie sie **WeatherPage.xaml**.

    ![Hinzufügen einer neuen Seite für Xamarin.Forms XAML](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

     Xamarin.Forms ist XAML-basiert, daher wird mit diesem Schritt eine **WeatherPage.xaml** -Datei zusammen mit der geschachtelten CodeBehind-Datei **WeatherPage.xaml.cs**erstellt. Sie können die Logik der Benutzeroberfläche in XAML oder Code schreiben. In dieser exemplarischen Vorgehensweise werden Teile beider Methoden verwendet.

2.  Um eine Schaltfläche zur **WeatherPage**-Anzeige hinzuzufügen, ersetzen Sie den Inhalt von **WeatherPage.xaml** durch folgendes Markup:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">
      <Button x:Name="getWeatherBtn"
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />
    </ContentPage>
    ```

     Beachten Sie, dass der Name der Schaltfläche mit dem `x:Name`-Attribut definiert werden muss, sodass Sie aus der CodeBehind-Datei heraus anhand des Namens auf diese Schaltfläche verweisen können.

3.  Zum Hinzufügen eines Ereignishandlers für das `Clicked`-Ereignis der Schaltfläche, um den Text der Schaltfläche zu aktualisieren, ersetzen Sie den Inhalt von **WeatherPage.xaml.cs** durch den unten stehenden Code. (Sie können „60601“ natürlich in eine andere Postleitzahl ändern.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();

                //Set the default binding to a default object for now
                BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Um **WeatherPage** als erste Anzeige beim Starten der App zu öffnen, ersetzen Sie den Standardkonstruktor in *App.xaml.cs* durch den folgenden Code:

    ```csharp
    public App()
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Erstellen Sie das Projekt **WeatherApp**, um sicherzustellen, dass der Code korrekt ist.

<a name="test" />

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Testen der App mit dem Visual Studio-Emulator für Android

Nun können Sie die App ausführen. Führen Sie zunächst nur die Android-Version aus, um zu überprüfen, ob die App Daten vom Wetterdienst empfängt. Nachdem Sie weitere Benutzeroberflächenelemente hinzugefügt haben, führen Sie auch die iOS- und UWP-Versionen aus.

1.  Legen Sie das **WeatherApp.Android**-Projekt als Startprojekt fest, indem Sie mit der rechten Maustaste darauf klicken und **Als Startprojekt festlegen** auswählen.

2.  In der Visual Studio-Symbolleiste ist **WeatherApp.Android** als Zielprojekt aufgeführt. Wählen Sie einen der Android-Emulatoren für das Debuggen aus, und drücken Sie **F5**. Es wird empfohlen, eine der **VisualStudio**-Emulatoroptionen zu verwenden, die die App im Visual Studio-Emulator für Android ausführen.

    ![Auswählen eines Debugziels für den Android-Emulator](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Wenn Visual Studio anzeigt, dass das Android-Projekt die Datei „Newtonsoft.Json“ nicht finden kann, fügen Sie das NuGet-Paket zum Android-Projekt hinzu.

3.  Wenn die App im Emulator gestartet wird, klicken Sie auf die **Wetter abrufen** -Schaltfläche. Der Text der Schaltfläche sollte zu **Chicago** aktualisiert werden, was die Eigenschaft `Title` der beim Wetterdatendienst abgerufenen Daten darstellt.

     ![WeatherApp vor und nach dem Tippen der Schaltfläche](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

<a name="finish" />

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Fertigstellen der Benutzeroberfläche mit einem homogenen Aussehen und Verhalten über Plattformen hinweg

Xamarin.Forms rendert systemeigene Benutzeroberflächen-Steuerelemente für jede Plattform, damit die App automatisch ein homogenes Aussehen und Verhalten aufweist. Sie können dieses native Aussehen und Verhalten besser erkennen, indem Sie die Benutzeroberfläche mit einem Eingabefeld für eine Postleitzahl und Steuerelementen zur Anzeige von Wetterdaten fertigstellen.

1.  Ersetzen Sie den Inhalt von **WeatherPage.xaml** durch das unten stehende Markup. Elemente, die wie zuvor beschrieben mit dem `x:Name`-Attribut benannt werden, können vom Code aus auf das Element verwiesen werden. Xamarin.Forms stellt außerdem eine Reihe von [Layoutoptionen](/xamarin/xamarin-forms/user-interface/controls/layouts) zur Verfügung. Hier verwendet WeatherPage [Raster](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) und [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>

                <Label Text="Search by Zip Code"
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />

                <Label x:Name="zipCodeLabel" Text="Zip Code:"
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />

                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />

                <Button x:Name="getWeatherBtn" Text="Get Weather"
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>
     ```

     Mithilfe des `OnPlatform`-Tags in XAML-Dateien können Sie einen Eigenschaftswert auswählen, der spezifisch für die aktuelle Plattform ist, auf der die App ausgeführt wird (siehe [Grundlegende XAML-Syntax](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/). Dieser Vorgang wird hier jedoch nicht dargestellt. In der CodeBehind-Datei können Sie feststellen, auf welcher Plattform die Anwendung läuft, indem Sie die Eigenschaft [`Device.RuntimePlatform`](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) mit Konstanten vergleichen, die in der Klasse [`Device`](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) mit den Namen [`Device.iOS`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [`Device.Android`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/) und [`Device.UWP`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/) definiert sind.

2.  Ersetzen Sie in *WeatherPage.xaml.cs* den `GetWeatherBtn_Clicked`-Ereignishandler durch den unten stehenden Code. Dieser Code überprüft, ob eine Postleitzahl im Eingabefeld vorhanden ist und ruft die Daten für diese Postleitzahl ab. Er setzt dann den Bindungskontext der gesamten Seite auf die sich daraus ergebende `Weather`-Instanz. Der Code schließt, indem der Tastentext auf „Erneut suchen“ gesetzt wird. Jede Bezeichnung in der Benutzeroberfläche ist an eine Eigenschaft der `Weather`-Klasse gebunden. Wenn Sie den Bindungskontext der Anzeige auf eine `Weather`-Instanz setzen, werden diese Bezeichnungen automatisch aktualisiert.

    ```csharp
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            BindingContext = weather;
            getWeatherBtn.Text = "Search Again";
        }
    }
    ```

3.  Führen Sie die App auf allen drei Plattformen aus, indem Sie mit der rechten Maustaste auf das entsprechende Projekt klicken, die Option **Als Startprojekt festlegen** auswählen und die App entweder auf einem Gerät oder im Emulator starten. Geben Sie eine gültige fünfstellige US-Postleitzahl ein, und klicken Sie auf die Schaltfläche **Wetter abrufen**, um Wetterdaten für diese Region anzuzeigen. Visual Studio muss mit einem Mac-Computer in Ihrem Netzwerk für das iOS-Projekt verbunden sein.

     [![Beispiel für eine Wetter-App unter iOS, Android und Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "Plattformübergreifender Leitfaden für Xamarin.Forms – 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Der vollständige Quellcode dieses Projekts befindet sich im [Repository „xamarin-forms-samples“ auf GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
