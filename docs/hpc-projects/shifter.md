# Shifter


Shifter is primarily maintained by NERSC at LBNL.  The repo can be found at https://github.com/nersc/shifter.
Shifter was the first HPC Container Runtime (as far as we are aware). It uses the standard Docker/OCI image 
format and uses a gateway service to pull and convert those images into an internal squash file that is used
by the runtime.  The gateway now uses stock CNCF/OCI tools for all of the image handling (e.g. skopeo, umoci,
oci-image-tool).  So assuming those tools are compliant, Shifter should be able to handle changes in the Spec.
So Shifter is compatible with the Image spec but it pretty much ignores the runtime spec and does its own thing.
