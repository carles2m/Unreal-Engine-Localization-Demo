# Unreal Engine Localization Demo / Proof of Concept

Minimalist demo showcasing plural and gender text formatting as per the official documentation in <https://docs.unrealengine.com/5.3/text-localization-in-unreal-engine/#textformatting>.

![Screenshot of the Localization Demo project running](https://github.com/carles2m/Unreal-Engine-Localization-Demo/assets/6278337/ca27920f-17f8-461a-a14f-2599c8db0eba)

## Running the Demo

Play in "Standalone Game" mode for changing languages to work.

![Screenshot of the menu in Unreal Engine where the Play Mode can be changed](https://github.com/carles2m/Unreal-Engine-Localization-Demo/assets/6278337/7ad526df-3ebe-4fef-8324-8d00c537e12e)

## Unreal Engine text formatting behavior

A language may not use a variable (for example, Gender) and other languages using it work as expected. Examples:

1. English: `"The warrior is strong"`. Spanish: `"{Gender}|gender(El guerrero,La guerrera,El guerrere) es fuerte"`.
    - For Gender=Femenine:
        - English text will ignore the Gender variable and show `"The warrior is strong"`.
        - Spanish text will use it: `"La guerrera es fuerte"`.

1. English: `"You came {Number}{Number}|ordinal(one=st,two=nd,few=rd,other=th)!"`. Spanish: `"¡Llegaste {Number}{Gender}|gender(o,a,e)!"`.
    - For Gender=Femenine and Number=2:
        - English text will ignore the Gender variable and just use the Number one showing `"You came 2nd!"`.
        - Spanish text will use both variables: `"¡Llegaste 2a!"`.

## Features

- The project contains the [BP_FormattedText Blueprint](Content/MainMenu/BP_FormattedText) to facilitate formatting a TextBlock preserving the original text in memory for reformatting in the fly when a variable is changed.

![Screenshot of blueprint BP_FormattedText logic](https://github.com/carles2m/Unreal-Engine-Localization-Demo/assets/6278337/ffb9c3dd-9aad-46ef-ae95-857c5dcd1b78)

## Troubleshooting

- In the Localization Dashboard actions "Gather Text", "Count Words" and "Compile Text" don't work - are running forever.
  - There is a bug in these Unreal Engine actions where the project file must not contain any space or special character.
