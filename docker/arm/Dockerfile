FROM cmosh/alpine-arm:edge
ENTRYPOINT ["/bin/matterbridge"]

COPY . /go/src/github.com/42wim/matterbridge
RUN apk update
RUN apk add go git gcc musl-dev ca-certificates
RUN cd /go/src/github.com/42wim/matterbridge
RUN export GOPATH=/go
RUN go get
RUN go build -x -ldflags "-X main.githash=$(git log --pretty=format:'%h' -n 1)" -o /bin/matterbridge
RUN rm -rf /go
RUN apk del --purge git go gcc musl-dev
