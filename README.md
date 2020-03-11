# Buildpack Tesseract

This package provide a custom Heroku buildpack providing the [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) binary and all the required libraries to Heroku apps. Training data for English language is provided by default (can be configured). 

## Configuration

The first step consists in allowing your Heroku app to use multiple buildpacks. Heroku natively supports [multiple buildpacks per app](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

1. setup your app as  
    ```
    heroku buildpacks:add --index 1 https://github.com/cofacts/heroku-buildpack-tesseract
    heroku buildpacks:set heroku/LANG
    ```
	
    where `LANG` is the language used by your app (e.g., `ruby`, `python`, or `nodejs`). A complete list of Heroku buildpacks can be found [here](https://devcenter.heroku.com/articles/buildpacks).
    
    > Note : You should make sure `heroku/nodejs` is initilized([execution order](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app#adding-a-buildpack)) after `heroku-buildpack-tesseract`, or npm [automatically run](https://devcenter.heroku.com/changelog-items/1557) will not work.
1. If you want Tesseract to be able to work with any other languages than English, set the environment variable `TESSERACT_OCR_LANGUAGES` to a comma-separated string of [ISO 639-2 language codes](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes).  
    ```bash
    $ heroku config:set TESSERACT_OCR_LANGUAGES="chi_tra"
    ```
1. Push your code to Heroku
1. You can use the `tesseract` binary in your Heroku app!

## Note
This fork upgrades Tesseract binary version from 4.0 to 4.1.1

## License
MIT License.

Original work Copyright (c) 2013 Marco Azimonti  
Modified work Copyright (c) 2015 Matteo Maggioni  
Modified work Copyright (c) 2017 Oswell Chan
Modified work Copyright (c) 2020 Diogo Watson
