classdef MatLabCalc < matlab.apps.AppBase

    % Properties that correspond to app components
    properties (Access = public)
        UIFigure           matlab.ui.Figure
        AEditFieldLabel    matlab.ui.control.Label
        InputA             matlab.ui.control.NumericEditField
        BEditFieldLabel    matlab.ui.control.Label
        InputB             matlab.ui.control.NumericEditField
        Subtract           matlab.ui.control.Button
        ResultField        matlab.ui.control.NumericEditField
        Divide             matlab.ui.control.Button
        SqrtAButton        matlab.ui.control.Button
        SqrtBButton        matlab.ui.control.Button
        ForceA2Button      matlab.ui.control.Button
        Multiply           matlab.ui.control.Button
        Sum                matlab.ui.control.Button
        ClearAButton       matlab.ui.control.Button
        ClearBButton       matlab.ui.control.Button
        ForceB2Button      matlab.ui.control.Button
        AforceB            matlab.ui.control.Button
        BforceA            matlab.ui.control.Button
        FactorialAButton   matlab.ui.control.Button
        FactorialB         matlab.ui.control.Button
        TanBButton         matlab.ui.control.Button
        CotBButton         matlab.ui.control.Button
        CosBButton         matlab.ui.control.Button
        SinBButton         matlab.ui.control.Button
        SinAButton         matlab.ui.control.Button
        CosAButton         matlab.ui.control.Button
        TanAButton         matlab.ui.control.Button
        CotAButton         matlab.ui.control.Button
        ClearScreenButton  matlab.ui.control.Button
        IncrementA         matlab.ui.control.Button
        DecrementA         matlab.ui.control.Button
        IncrementB         matlab.ui.control.Button
        DecrementB         matlab.ui.control.Button
        OnOffSwitch        matlab.ui.control.Switch
    end

    properties (Access = private)
        PropertyA = 0; % Globalne zmiennie przechowujące liczby 
        PropertyB = 0;  
    end

    % Callbacks that handle component events
    methods (Access = private)

        % Button pushed function: ClearAButton
        function ClearAButtonPushed(app, event)
            %czyszczenie wartości pola liczby A
            app.InputA.Value = 0; 
        end

        % Button pushed function: ClearBButton
        function ClearBButtonPushed(app, event)
               %czyszczenie wartości pola liczby B
            app.InputB.Value = 0;
        end

        % Value changed function: InputA
        function InputAValueChanged(app, event)
            %przypisywanie wartości liczbowej polu A
            value = app.InputA.Value;
            app.PropertyA = value;
        end

        % Value changed function: InputB
        function InputBValueChanged(app, event)
            %przypisywanie wartości liczbowej polu A
            value = app.InputB.Value;
            app.PropertyB = value;
        end

        % Button pushed function: Subtract
        function SubtractButtonPushed(app, event)
            %elementarna operacja odejmowania 
            app.ResultField.Value = app.PropertyA - app.PropertyB;
            disp(app.ResultField.Value);
        end

        % Button pushed function: ClearScreenButton
        function ClearScreenButtonPushed(app, event)
            %Czyszczenie wartości pola wynikowego
            app.ResultField.Value = 0;
        end

        % Button pushed function: Multiply
        function MultiplyButtonPushed(app, event)
            %elementarna operacja mnożenia
            app.ResultField.Value = app.PropertyA * app.PropertyB;
            disp(app.ResultField.Value);
        end

        % Button pushed function: Divide
        function DivideButtonPushed(app, event)
            %elementarna operacja dzielenia
            app.ResultField.Value = app.PropertyA / app.PropertyB;
            disp(app.ResultField.Value);
        end

        % Value changed function: OnOffSwitch
        function OnOffSwitchValueChanged(app, event)
            %Ukrywanie widoczności okienka aplikacji za pomocą przycisku,
            %widoczność okna aplikacji zależna jest od wartości pola
            %Visible komponentu
            value = app.OnOffSwitch.Value;
            if strcmp(value , "On")
                app.UIFigure.Visible = "on";
            else 
                app.UIFigure.Visible = "off";
                
            end
        end

        % Button pushed function: ForceA2Button
        function ForceA2ButtonPushed(app, event)
            %druga potęga liczbyA
            app.ResultField.Value = app.PropertyA ^ 2;
            disp(app.ResultField.Value);
        end

        % Button pushed function: ForceB2Button
        function ForceB2ButtonPushed(app, event)
            %druga potęga liczby B
            app.ResultField.Value = app.PropertyB ^ 2;
            disp(app.ResultField.Value); 
        end

        % Button pushed function: AforceB
        function AforceBButtonPushed(app, event)
            %B-eta potęga liczby A
            app.ResultField.Value = app.PropertyA ^ app.PropertyB;
            disp(app.ResultField.Value); 
        end

        % Button pushed function: BforceA
        function BforceAButtonPushed(app, event)
            %A-ta potęga liczby B
            app.ResultField.Value = app.PropertyB ^ app.PropertyA;
            disp(app.ResultField.Value); 
        end

        % Button pushed function: IncrementA
        function IncrementAButtonPushed(app, event)
            %Inkrementacja wartości pola A
            app.PropertyA = 1 + app.PropertyA;
            app.InputA.Value = app.PropertyA;
        end

        % Button pushed function: IncrementB
        function IncrementBButtonPushed(app, event)
            %Inkrementacja wartości pola B
            app.PropertyB = 1 + app.PropertyB;
            app.InputB.Value = app.PropertyB;
        end

        % Button pushed function: DecrementA
        function DecrementAButtonPushed(app, event)
            %Dekrementacja wartości pola A
            app.PropertyA = app.PropertyA - 1;
            app.InputA.Value = app.PropertyA;
        end

        % Button pushed function: DecrementB
        function DecrementBButtonPushed(app, event)
            %Dekrementacja wartości pola B
            app.PropertyB = app.PropertyB - 1;
            app.InputB.Value = app.PropertyB;
        end

        % Button pushed function: SqrtAButton
        function SqrtAButtonPushed(app, event)
            %Pierwiastek kwadratowy z liczby A
            app.ResultField.Value = sqrt(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: SqrtBButton
        function SqrtBButtonPushed(app, event)
            %Pierwiastek kwadratowy z liczby B
            app.ResultField.Value = sqrt(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: FactorialAButton
        function FactorialAButtonPushed(app, event)
            %silnia z liczby A
            app.ResultField.Value = factorial(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: FactorialB
        function FactorialBButtonPushed(app, event)
            %Silnia z liczby B 
            app.ResultField.Value = factorial(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: TanBButton
        function TanBButtonPushed(app, event)
            %Obliczenie wartości tangensa z liczby B
            app.ResultField.Value = tan(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: TanAButton
        function TanAButtonPushed(app, event)
            %Obliczenie wartości tangensa z liczby A
            app.ResultField.Value = tan(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: CotBButton
        function CotBButtonPushed(app, event)
            %Obliczenie wartości cotangensa z liczby B
            app.ResultField.Value = cot(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: CotAButton
        function CotAButtonPushed(app, event)
            %Obliczenie wartości cotangensa z liczby A
            app.ResultField.Value = cot(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: SinBButton
        function SinBButtonPushed(app, event)
            %Obliczenie wartości sinusa z liczby B
            app.ResultField.Value = sin(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: SinAButton
        function SinAButtonPushed(app, event)
            %Obliczenie wartości sinusa z liczby A
            app.ResultField.Value = sin(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: CosBButton
        function CosBButtonPushed(app, event)
            %Obliczenie wartości cosinusa z liczby B
            app.ResultField.Value = cos(app.PropertyB);
            disp(app.ResultField.Value);
        end

        % Button pushed function: CosAButton
        function CosAButtonPushed(app, event)
            %Obliczenie wartości cosinusa z liczby A
            app.ResultField.Value = cos(app.PropertyA);
            disp(app.ResultField.Value);
        end

        % Button pushed function: Sum
        function SumButtonPushed(app, event)
            %elementarna operacja dodawania 
            app.ResultField.Value = app.PropertyA + app.PropertyB;
            disp(app.ResultField.Value);
        end
    end

    % Component initialization
    methods (Access = private)

        % Create UIFigure and components
        function createComponents(app)

            % Create UIFigure and hide until all components are created
            app.UIFigure = uifigure('Visible', 'off');
            app.UIFigure.Color = [0.149 0.149 0.149];
            app.UIFigure.Position = [100 100 640 480];
            app.UIFigure.Name = 'MATLAB App';

            % Create AEditFieldLabel
            app.AEditFieldLabel = uilabel(app.UIFigure);
            app.AEditFieldLabel.HorizontalAlignment = 'right';
            app.AEditFieldLabel.FontColor = [1 1 1];
            app.AEditFieldLabel.Position = [3 425 25 22];
            app.AEditFieldLabel.Text = 'A';

            % Create InputA
            app.InputA = uieditfield(app.UIFigure, 'numeric');
            app.InputA.ValueChangedFcn = createCallbackFcn(app, @InputAValueChanged, true);
            app.InputA.FontWeight = 'bold';
            app.InputA.Position = [34 425 100 22];

            % Create BEditFieldLabel
            app.BEditFieldLabel = uilabel(app.UIFigure);
            app.BEditFieldLabel.HorizontalAlignment = 'right';
            app.BEditFieldLabel.FontColor = [1 1 1];
            app.BEditFieldLabel.Position = [3 397 25 22];
            app.BEditFieldLabel.Text = 'B';

            % Create InputB
            app.InputB = uieditfield(app.UIFigure, 'numeric');
            app.InputB.ValueChangedFcn = createCallbackFcn(app, @InputBValueChanged, true);
            app.InputB.FontWeight = 'bold';
            app.InputB.Position = [34 397 100 22];

            % Create Subtract
            app.Subtract = uibutton(app.UIFigure, 'push');
            app.Subtract.ButtonPushedFcn = createCallbackFcn(app, @SubtractButtonPushed, true);
            app.Subtract.BackgroundColor = [1 0.4314 0.1686];
            app.Subtract.FontSize = 25;
            app.Subtract.FontColor = [1 1 1];
            app.Subtract.Position = [551 25 56 54];
            app.Subtract.Text = '-';

            % Create ResultField
            app.ResultField = uieditfield(app.UIFigure, 'numeric');
            app.ResultField.FontWeight = 'bold';
            app.ResultField.Position = [308 374 299 73];

            % Create Divide
            app.Divide = uibutton(app.UIFigure, 'push');
            app.Divide.ButtonPushedFcn = createCallbackFcn(app, @DivideButtonPushed, true);
            app.Divide.BackgroundColor = [1 0.4314 0.1686];
            app.Divide.FontSize = 25;
            app.Divide.FontColor = [1 1 1];
            app.Divide.Position = [551 86 56 54];
            app.Divide.Text = '÷';

            % Create SqrtAButton
            app.SqrtAButton = uibutton(app.UIFigure, 'push');
            app.SqrtAButton.ButtonPushedFcn = createCallbackFcn(app, @SqrtAButtonPushed, true);
            app.SqrtAButton.BackgroundColor = [1 0.4314 0.1686];
            app.SqrtAButton.FontSize = 18;
            app.SqrtAButton.FontColor = [1 1 1];
            app.SqrtAButton.Position = [486 151 56 54];
            app.SqrtAButton.Text = 'SqrtA';

            % Create SqrtBButton
            app.SqrtBButton = uibutton(app.UIFigure, 'push');
            app.SqrtBButton.ButtonPushedFcn = createCallbackFcn(app, @SqrtBButtonPushed, true);
            app.SqrtBButton.BackgroundColor = [1 0.4314 0.1686];
            app.SqrtBButton.FontSize = 18;
            app.SqrtBButton.FontColor = [1 1 1];
            app.SqrtBButton.Position = [551 151 56 54];
            app.SqrtBButton.Text = 'SqrtB';

            % Create ForceA2Button
            app.ForceA2Button = uibutton(app.UIFigure, 'push');
            app.ForceA2Button.ButtonPushedFcn = createCallbackFcn(app, @ForceA2ButtonPushed, true);
            app.ForceA2Button.BackgroundColor = [1 0.4314 0.1686];
            app.ForceA2Button.FontSize = 25;
            app.ForceA2Button.FontColor = [1 1 1];
            app.ForceA2Button.Position = [32 86 73 54];
            app.ForceA2Button.Text = 'a^2';

            % Create Multiply
            app.Multiply = uibutton(app.UIFigure, 'push');
            app.Multiply.ButtonPushedFcn = createCallbackFcn(app, @MultiplyButtonPushed, true);
            app.Multiply.BackgroundColor = [1 0.4314 0.1686];
            app.Multiply.FontSize = 25;
            app.Multiply.FontColor = [1 1 1];
            app.Multiply.Position = [486 86 56 54];
            app.Multiply.Text = 'x';

            % Create Sum
            app.Sum = uibutton(app.UIFigure, 'push');
            app.Sum.ButtonPushedFcn = createCallbackFcn(app, @SumButtonPushed, true);
            app.Sum.BackgroundColor = [1 0.4314 0.1686];
            app.Sum.FontSize = 25;
            app.Sum.FontColor = [1 1 1];
            app.Sum.Position = [486 25 56 54];
            app.Sum.Text = '+';

            % Create ClearAButton
            app.ClearAButton = uibutton(app.UIFigure, 'push');
            app.ClearAButton.ButtonPushedFcn = createCallbackFcn(app, @ClearAButtonPushed, true);
            app.ClearAButton.FontWeight = 'bold';
            app.ClearAButton.Position = [206 423 78 21];
            app.ClearAButton.Text = 'ClearA';

            % Create ClearBButton
            app.ClearBButton = uibutton(app.UIFigure, 'push');
            app.ClearBButton.ButtonPushedFcn = createCallbackFcn(app, @ClearBButtonPushed, true);
            app.ClearBButton.FontWeight = 'bold';
            app.ClearBButton.Position = [206 395 78 22];
            app.ClearBButton.Text = 'ClearB';

            % Create ForceB2Button
            app.ForceB2Button = uibutton(app.UIFigure, 'push');
            app.ForceB2Button.ButtonPushedFcn = createCallbackFcn(app, @ForceB2ButtonPushed, true);
            app.ForceB2Button.BackgroundColor = [1 0.4314 0.1686];
            app.ForceB2Button.FontSize = 25;
            app.ForceB2Button.FontColor = [1 1 1];
            app.ForceB2Button.Position = [32 25 73 54];
            app.ForceB2Button.Text = 'b^2';

            % Create AforceB
            app.AforceB = uibutton(app.UIFigure, 'push');
            app.AforceB.ButtonPushedFcn = createCallbackFcn(app, @AforceBButtonPushed, true);
            app.AforceB.BackgroundColor = [1 0.4314 0.1686];
            app.AforceB.FontSize = 25;
            app.AforceB.FontColor = [1 1 1];
            app.AforceB.Position = [110 86 73 54];
            app.AforceB.Text = 'a^b';

            % Create BforceA
            app.BforceA = uibutton(app.UIFigure, 'push');
            app.BforceA.ButtonPushedFcn = createCallbackFcn(app, @BforceAButtonPushed, true);
            app.BforceA.BackgroundColor = [1 0.4314 0.1686];
            app.BforceA.FontSize = 25;
            app.BforceA.FontColor = [1 1 1];
            app.BforceA.Position = [110 25 73 54];
            app.BforceA.Text = 'b^a';

            % Create FactorialAButton
            app.FactorialAButton = uibutton(app.UIFigure, 'push');
            app.FactorialAButton.ButtonPushedFcn = createCallbackFcn(app, @FactorialAButtonPushed, true);
            app.FactorialAButton.BackgroundColor = [1 0.4314 0.1686];
            app.FactorialAButton.FontSize = 18;
            app.FactorialAButton.FontColor = [1 1 1];
            app.FactorialAButton.Position = [486 214 56 54];
            app.FactorialAButton.Text = 'A!';

            % Create FactorialB
            app.FactorialB = uibutton(app.UIFigure, 'push');
            app.FactorialB.ButtonPushedFcn = createCallbackFcn(app, @FactorialBButtonPushed, true);
            app.FactorialB.BackgroundColor = [1 0.4314 0.1686];
            app.FactorialB.FontSize = 18;
            app.FactorialB.FontColor = [1 1 1];
            app.FactorialB.Position = [551 214 56 54];
            app.FactorialB.Text = 'B!';

            % Create TanBButton
            app.TanBButton = uibutton(app.UIFigure, 'push');
            app.TanBButton.ButtonPushedFcn = createCallbackFcn(app, @TanBButtonPushed, true);
            app.TanBButton.BackgroundColor = [1 0.4314 0.1686];
            app.TanBButton.FontSize = 18;
            app.TanBButton.FontColor = [1 1 1];
            app.TanBButton.Position = [353 25 56 54];
            app.TanBButton.Text = 'TanB';

            % Create CotBButton
            app.CotBButton = uibutton(app.UIFigure, 'push');
            app.CotBButton.ButtonPushedFcn = createCallbackFcn(app, @CotBButtonPushed, true);
            app.CotBButton.BackgroundColor = [1 0.4314 0.1686];
            app.CotBButton.FontSize = 18;
            app.CotBButton.FontColor = [1 1 1];
            app.CotBButton.Position = [420 25 56 54];
            app.CotBButton.Text = 'CotB';

            % Create CosBButton
            app.CosBButton = uibutton(app.UIFigure, 'push');
            app.CosBButton.ButtonPushedFcn = createCallbackFcn(app, @CosBButtonPushed, true);
            app.CosBButton.BackgroundColor = [1 0.4314 0.1686];
            app.CosBButton.FontSize = 18;
            app.CosBButton.FontColor = [1 1 1];
            app.CosBButton.Position = [419 86 59 54];
            app.CosBButton.Text = 'CosB';

            % Create SinBButton
            app.SinBButton = uibutton(app.UIFigure, 'push');
            app.SinBButton.ButtonPushedFcn = createCallbackFcn(app, @SinBButtonPushed, true);
            app.SinBButton.BackgroundColor = [1 0.4314 0.1686];
            app.SinBButton.FontSize = 18;
            app.SinBButton.FontColor = [1 1 1];
            app.SinBButton.Position = [353 86 56 54];
            app.SinBButton.Text = 'SinB';

            % Create SinAButton
            app.SinAButton = uibutton(app.UIFigure, 'push');
            app.SinAButton.ButtonPushedFcn = createCallbackFcn(app, @SinAButtonPushed, true);
            app.SinAButton.BackgroundColor = [1 0.4314 0.1686];
            app.SinAButton.FontSize = 18;
            app.SinAButton.FontColor = [1 1 1];
            app.SinAButton.Position = [353 214 56 54];
            app.SinAButton.Text = 'SinA';

            % Create CosAButton
            app.CosAButton = uibutton(app.UIFigure, 'push');
            app.CosAButton.ButtonPushedFcn = createCallbackFcn(app, @CosAButtonPushed, true);
            app.CosAButton.BackgroundColor = [1 0.4314 0.1686];
            app.CosAButton.FontSize = 18;
            app.CosAButton.FontColor = [1 1 1];
            app.CosAButton.Position = [419 214 59 54];
            app.CosAButton.Text = 'CosA';

            % Create TanAButton
            app.TanAButton = uibutton(app.UIFigure, 'push');
            app.TanAButton.ButtonPushedFcn = createCallbackFcn(app, @TanAButtonPushed, true);
            app.TanAButton.BackgroundColor = [1 0.4314 0.1686];
            app.TanAButton.FontSize = 18;
            app.TanAButton.FontColor = [1 1 1];
            app.TanAButton.Position = [353 151 56 54];
            app.TanAButton.Text = 'TanA';

            % Create CotAButton
            app.CotAButton = uibutton(app.UIFigure, 'push');
            app.CotAButton.ButtonPushedFcn = createCallbackFcn(app, @CotAButtonPushed, true);
            app.CotAButton.BackgroundColor = [1 0.4314 0.1686];
            app.CotAButton.FontSize = 18;
            app.CotAButton.FontColor = [1 1 1];
            app.CotAButton.Position = [420 151 56 54];
            app.CotAButton.Text = 'CotA';

            % Create ClearScreenButton
            app.ClearScreenButton = uibutton(app.UIFigure, 'push');
            app.ClearScreenButton.ButtonPushedFcn = createCallbackFcn(app, @ClearScreenButtonPushed, true);
            app.ClearScreenButton.FontWeight = 'bold';
            app.ClearScreenButton.Position = [507 342 100 22];
            app.ClearScreenButton.Text = 'Clear Screen';

            % Create IncrementA
            app.IncrementA = uibutton(app.UIFigure, 'push');
            app.IncrementA.ButtonPushedFcn = createCallbackFcn(app, @IncrementAButtonPushed, true);
            app.IncrementA.FontWeight = 'bold';
            app.IncrementA.Position = [142 423 26 22];
            app.IncrementA.Text = '+';

            % Create DecrementA
            app.DecrementA = uibutton(app.UIFigure, 'push');
            app.DecrementA.ButtonPushedFcn = createCallbackFcn(app, @DecrementAButtonPushed, true);
            app.DecrementA.FontWeight = 'bold';
            app.DecrementA.Position = [174 423 26 22];
            app.DecrementA.Text = '-';

            % Create IncrementB
            app.IncrementB = uibutton(app.UIFigure, 'push');
            app.IncrementB.ButtonPushedFcn = createCallbackFcn(app, @IncrementBButtonPushed, true);
            app.IncrementB.FontWeight = 'bold';
            app.IncrementB.Position = [142 397 26 22];
            app.IncrementB.Text = '+';

            % Create DecrementB
            app.DecrementB = uibutton(app.UIFigure, 'push');
            app.DecrementB.ButtonPushedFcn = createCallbackFcn(app, @DecrementBButtonPushed, true);
            app.DecrementB.FontWeight = 'bold';
            app.DecrementB.Position = [174 397 26 22];
            app.DecrementB.Text = '-';

            % Create OnOffSwitch
            app.OnOffSwitch = uiswitch(app.UIFigure, 'slider');
            app.OnOffSwitch.Items = {'On', 'Off'};
            app.OnOffSwitch.ValueChangedFcn = createCallbackFcn(app, @OnOffSwitchValueChanged, true);
            app.OnOffSwitch.FontColor = [1 1 1];
            app.OnOffSwitch.Position = [534 305 45 20];
            app.OnOffSwitch.Value = 'On';

            % Show the figure after all components are created
            app.UIFigure.Visible = 'on';
        end
    end

    % App creation and deletion
    methods (Access = public)

        % Construct app
        function app = MatLabCalc

            % Create UIFigure and components
            createComponents(app)

            % Register the app with App Designer
            registerApp(app, app.UIFigure)

            if nargout == 0
                clear app
            end
        end

        % Code that executes before app deletion
        function delete(app)

            % Delete UIFigure when app is deleted
            delete(app.UIFigure)
        end
    end
end
