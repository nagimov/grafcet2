# grafcet2
LATEX package for drawing grafcets (sequential function charts)

    % ---------------------------------------------------------------------------- %
    %                                GRAFCET2 0.1                                  %
    % ---------------------------------------------------------------------------- %
    %         Ruslan Nagimov                                                       %
    %         github: http://nagimov.github.com/grafcet2/                          %
    %         e-mail: nagimov@outlook.com                                          %
    % ---------------------------------------------------------------------------- %
    % This package is based on Pierre Chatelier's GRAFCET package:                 %
    %         GRAFCET 1.0                                                          %
    %         e-mail: pierre.chatelier@club-internet.fr                            %
    %         web:    http://perso.club-internet.fr/ktd                            %
    % More commands were added, variable names and comments were translated to     %
    % English.                                                                     %
    % ---------------------------------------------------------------------------- %
    % This package allows to draw nice grafcets (sequential function charts) using %
    % latex.                                                                       %
    %                                                                              %
    % Required packages:                                                           %
    %     # float                                                                  %
    %     # ifthen                                                                 %
    %     # hhline                                                                 %
    % ---------------------------------------------------------------------------- %
    % The syntax of commands:                                                      %
    %                                                                              %
    %     \Transition{text}                                                        %
    %         Transition block represents the line, connecting two steps. The text %
    %         usually represents the condition which has to be met in order to     %
    %         proceed execution.                                                   %
    %                                                                              %
    %     \Step{text}                                                              %
    %         Step block represent the square, executing command.                  %
    %                                                                              %
    %     \FirstStep{text}                                                         %
    %         The same as \Step, drawn with a double line, used for the first step %
    %         in the function/routine.                                             %
    %                                                                              %
    %     \MacroStep{text}                                                         %
    %         The same as \Step, drawn with extra lines at a top and a bottom of   %
    %         the block.                                                           %
    %                                                                              %
    %     \Divergence{...}{...}                                                    %
    %         Divergence block is used to represent "OR" conditions. Creates       %
    %         single horizontal line.                                              %
    %                                                                              %
    %     \Fork{...}{...}                                                          %
    %         Fork block is used to represent "AND" conditions (parallel           %
    %         processing). Creates double horizontal line.                         %
    %                                                                              %
    %     \Loop{...}                                                               %
    %         Loop block is used to create cycled execution path.                  %
    %                                                                              %
    %     \Nop                                                                     %
    %         Creates blank space with vertical line (useful for filling blank     %
    %         steps after forks).                                                  %
    % ---------------------------------------------------------------------------- %
    %                                                                              %
    %                     Pseudographic explanation of commands                    %
    %                                                                              %
    %                     ╔═════════════╗                                          %
    %                     ║             ║                                          %
    %                     ║ First  Step ║                                          %
    %                     ║             ║                                          %
    %                     ╚══════╤══════╝                                          %
    %                            │                                                 %
    %                            │                                                 %
    %                           ─┼─ Transition                                     %
    %                            │                                                 %
    %                            │                                                 %
    %                     ───────┼─────────────────────┬───────  # Divergence      %
    %                            │                     │                           %
    %                            │                     │                           %
    %                     ┌──────┴──────┐       ┌──────┴──────┐\                   %
    %                     ├─────────────┤       │             │ \                  %
    %                     │ Macro  Step │       │  Jump Step  │  >                 %
    %                     ├─────────────┤       │             │ /                  %
    %                     └──────┬──────┘       └──────┬──────┘/                   %
    %                            │                     │                           %
    %                            │                     │                           %
    %                     ───────┼─────────────────────┴───────                    %
    %                            │                                                 %
    %                            │                                                 %
    %                            │                                                 %
    %                            │                                                 %
    %                     ═══════╪═════════════════════╤═══════  # Fork            %
    %                            │                     │                           %
    %                            │                     │                           %
    %                     ┌──────┴──────┐       ┌──────┴──────┐                    %
    %                     │             │       │             │                    %
    %                     │    Step     │       │    Step     │                    %
    %                     │             │       │             │                    %
    %                     └──────┬──────┘       └──────┬──────┘                    %
    %                            │                     │                           %
    %                            │                     │                           %
    %                     ═══════╪═════════════════════╧═══════                    %
    %                            │                                                 %
    %                            │                                                 %
    %                            │                                                 %
    %                            │                                                 %
    %                            │<───────────┐  # Loop                            %
    %                            │            │                                    %
    %                            │            │                                    %
    %                     ┌──────┴──────┐     │                                    %
    %                     │             │     │                                    %
    %                     │    Step     │     ^                                    %
    %                     │             │     │                                    %
    %                     └──────┬──────┘     │                                    %
    %                            │            │                                    %
    %                            │            │                                    %
    %                            └──────>─────┘                                    %
    %                                                                              %
    % ---------------------------------------------------------------------------- %
