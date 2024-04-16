Hello Git and Github

from dash import html

radio_buttons = html.Div([
    html.Div(className='govuk-form-group', children=[
        html.Fieldset(className='govuk-fieldset', children=[
            html.Legend(className='govuk-fieldset__legend govuk-fieldset__legend--s', children='Do you want to accept functional cookies?'),
            html.Div(className='govuk-radios', children=[
                html.Div(className='govuk-radios__item', children=[
                    html.Input(
                        className='govuk-radios__input', 
                        id='cookies-functional', 
                        name='cookies[functional]', 
                        type='radio', 
                        value='yes'
                    ),
                    html.Label(
                        className='govuk-label govuk-radios__label', 
                        htmlFor='cookies-functional', 
                        children='Yes'
                    )
                ]),
                html.Div(className='govuk-radios__item', children=[
                    html.Input(
                        className='govuk-radios__input', 
                        id='cookies-functional-2', 
                        name='cookies[functional]', 
                        type='radio', 
                        value='no',
                        checked=True
                    ),
                    html.Label(
                        className='govuk-label govuk-radios__label', 
                        htmlFor='cookies-functional-2', 
                        children='No'
                    )
                ])
            ])
        ])
    ])
])

app.index_string = '''
<!DOCTYPE html>
<html lang="en" class="govuk-template">
  <head>
    {%metas%}
    <title>{%title%}</title>
    {%favicon%} {%css%}
    <!-- ... other head elements ... -->
  </head>
  <body class="govuk-template__body">
    <div class="govuk-cookie-banner" data-nosnippet role="region" aria-label="Cookies on Local Authority Data Explorer">
      <!-- ... banner content ... -->
    </div>
    
    <!-- ... other body content ... -->
    
    <script>
      // Consent management script
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}

      function updateConsent(consent) {
        localStorage.setItem('consentMode', JSON.stringify(consent));
        hideCookieBanner();
        gtag('consent', 'update', consent); // This will update the consent configuration
      }

      function acceptCookies() {
        updateConsent({
          'ad_storage': 'granted',
          'analytics_storage': 'granted',
          'personalization_storage': 'granted',
          'functionality_storage': 'granted',
          'security_storage': 'granted',
        });
      }

      function denyCookies() {
        updateConsent({
          'ad_storage': 'denied',
          'analytics_storage': 'denied',
          'personalization_storage': 'denied',
          'functionality_storage': 'denied',
          'security_storage': 'denied',
        });
      }

      function hideCookieBanner() {
        var banner = document.querySelector('.govuk-cookie-banner');
        if (banner) {
          banner.style.display = 'none';
        }
      }

      // Hide the banner or set default consent on initial load
      if(localStorage.getItem('consentMode')) {
          hideCookieBanner();
          gtag('consent', 'default', JSON.parse(localStorage.getItem('consentMode')));
      } else {
          // Set default denied consent if not already set
          denyCookies(); // Calls updateConsent with 'denied' state
      }
    </script>
    
    <!-- ... Google Tag Manager and noscript elements ... -->
    
  </body>
</html>
'''
