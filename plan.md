# Skill outline
- What/Why
    - The end game is to be able to use the `Alexa Smart Home Skill APIs` to interact with devices that alexa manages.
      This is not accessible directly but can be used within alexa skills.
      Additionally, you cannot write code to just "talk to alexa" to try to directly invoke alexa actions/intents
      An option that is available is to create a skill and make it backed by an AWS lambda function.
      In this situation, when the skill is invoked via alexa, it will make a request to the registered AWS lambda function.
      This AWS lamdba function is now allowed to interact with the Alexa Smart Home Skill APIs (which means it could control your lights/plugs).
      It is also possible to invoke this AWS Lambda function directly via HTTP.
      Meaning that, following this chain, we can use a HTTP request to talk to our Lambda function and toggle a smart home device.
      It will be the intention to trigger this HTTP request from home assistant so that I can use a zigbee device to trigger a device controlled by alexa.
      - Alexa Smart Home Skill APIs (https://developer.amazon.com/en-US/docs/alexa/device-apis/smart-home-general-apis.html)
        - Alexa.PowerController (Users can turn their smart home devices on and off.)
        - Alexa.BrightnessController (Users can control the brightness of devices, such as light bulbs.)
- Interface to manage skills
    - Alexa Developer Console (GUI to administrate them)
        - https://developer.amazon.com/alexa/console/ask
- Create a skill (using the developer console)
    - Inputs
        - skill must have a Custom Interaction Model
        - invocation name (doesnt matter, used for alexa to discern a voice command relates to this skill)
    - Output
        - alexa skill application ID
            - needed later......????
- Configure skill
    - setup intent schema (the schema that defines actions our skill implements) (# indicates required base intent)
        - TurnOn
        - TurnOff
        - Toggle
        - Status
        - *AMAZON.HelpIntent
        - *AMAZON.StopIntent
        - *AMAZON.CancelIntent
