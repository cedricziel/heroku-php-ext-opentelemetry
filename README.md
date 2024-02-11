# OpenTelemetry extensions for Heroku

This package provides PHP extensions for the OpenTelemetry SDK to enable collection
of compatible signals through auto-instrumentation.

## Usage

Set the `HEROKU_PHP_PLATFORM_REPOSITORIES` environment variable pointing to this (or your) repository.

Once set, heroku will install the extensions on the next deploy.

On Heroku:

```shell
heroku config:set --app=APP_NAME HEROKU_PHP_PLATFORM_REPOSITORIES="https://cedricziel.github.io/heroku-php-ext-opentelemetry/"
```

On dokku
    
```shell
dokku config:set --no-restart APP_NAME HEROKU_PHP_PLATFORM_REPOSITORIES="https://cedricziel.github.io/heroku-php-ext-opentelemetry/"
```

## Next steps

After installing the extensions, you can enable and configure auto-instrumentation in your application.

Please check the PHP auto-instrumentation documentation of the OpenTelemetry SDK for PHP for more information.

https://opentelemetry.io/docs/languages/php/automatic/

### Enable and configure auto-instrumentation

Set the following environment variables to enable and configure auto-instrumentation:

 * `OTEL_PHP_AUTOLOAD_ENABLED=true` to enable auto-instrumentation
 * `OTEL_SERVICE_NAME=your-service-name` to set the service name
 * `OTEL_TRACES_EXPORTER=otlp` to enable exporting traces to an OpenTelemetry Collector
 * `OTEL_EXPORTER_OTLP_PROTOCOL=grpc` to use gRPC
 * `OTEL_EXPORTER_OTLP_ENDPOINT=http://collector:4318` to set the endpoint of the OpenTelemetry Collector
 * `OTEL_PROPAGATORS=baggage,tracecontext` to enable baggage and trace context propagation

On Dokku:

```shell
dokku config:set --no-restart APP_NAME OTEL_PHP_AUTOLOAD_ENABLED=true \
    OTEL_SERVICE_NAME=your-service-name \
    OTEL_TRACES_EXPORTER=otlp \
    OTEL_EXPORTER_OTLP_PROTOCOL=http/protobuf \
    OTEL_EXPORTER_OTLP_ENDPOINT=http://collector:4318 \
    OTEL_PROPAGATORS=baggage,tracecontext
```

On Heroku:

```shell
dokku config:set --no-restart APP_NAME OTEL_PHP_AUTOLOAD_ENABLED=true \
    OTEL_SERVICE_NAME=your-service-name \
    OTEL_TRACES_EXPORTER=otlp \
    OTEL_EXPORTER_OTLP_PROTOCOL=http/protobuf \
    OTEL_EXPORTER_OTLP_ENDPOINT=http://collector:4318 \
    OTEL_PROPAGATORS=baggage,tracecontext
```

Learn more about the environment variables in the OpenTelemetry documentation: https://opentelemetry.io/docs/specs/otel/protocol/exporter/

### Install auto-instrumentation packages in your application

Find auto-instrumentation for PHP on Packagist: https://packagist.org/search/?query=open-telemetry&tags=instrumentation

## License

MIT
