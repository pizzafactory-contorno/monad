FROM golang:1.13.1-alpine3.10 as builder

#RUN mkdir -p /go/src/github.com/monasuire && \
RUN mkdir -p /go/src/github.com/monasuite && \
    apk --no-cache add git && \
    git clone https://github.com/monasuite/monad.git /go/src/github.com/monasuite/monad && \
    apk --no-cache del git && \
    cd /go/src/github.com/monasuite/monad && \
    GO111MODULE=on go install -v . ./cmd/... && \
    mkdir -p /root/.monad

FROM pizzafactory0contorno/piatto:alpine

RUN mkdir -p /home/user/.monad
COPY --from=builder /go/bin/addblock /go/bin/findcheckpoint /go/bin/gencerts /go/bin/monactl /go/bin/monad /usr/local/bin/
COPY --from=builder /go/src/github.com/monasuite/monad/sample-monad.conf /home/user/

EXPOSE 9400 9401 9402 9403 19400 19401 19402 19403
VOLUME /home/user/.monad

ENTRYPOINT [ "/usr/local/bin/monad" ]

LABEL maintainer="monaka@pizzafactory.jp"
