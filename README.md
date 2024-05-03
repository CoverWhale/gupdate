# gupdate

Create self updating binaries

## Background

This package wraps Minio's self updater package and allows for automatic downloading of Go binaries.

## Usage

Create a project and then use gupdate to get the latest release and update the binary.

```
gh := gupdate.GitHubProject{
	Name:     "coverwhale-go",
	Owner:    "CoverWhale",
	Platform: runtime.GOOS,
	Arch:     runtime.GOARCH,
	CheckSumGetter: gupdate.Goreleaser{},
}

release, err := gupdate.GetLatestRelease(gh)
if err != nil {
	log.Fatal(err)
}

if err := release.Update(); err != nil {
	log.Fatal(err)
}
```
